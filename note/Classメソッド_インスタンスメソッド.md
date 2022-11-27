
# Class  
Classはオブジェクトの種族を表す。  
自分でClassを作ると自分で種族を作ったことになる。  
Classに属するオブジェクトをそのClassのインスタンスとも言う。  
```  
<Class>.new #=> そのクラスの新しいオブジェクト(インスタンス)  
p String.new("wahaha") #=> "wahaha"  
```  
```  
<object>.class #=> オブジェクトのクラス確認  
p "wahaha".class #=> String
```  
クラスメソッドとインスタンスメソッドはレシーバーの違い。  
## クラスメソッド  
クラスメソッドはレシーバーがクラス。
つまりクラスに対して使うメソッド。`<Class>.new`など。  
`def self.<method>`のように`self`を付けて定義する。  
ドキュメントでは`Class.method`や`Class::method`のような形で表記される。  
```  
class <Class>
  def self.<method> # 定義する際はselfを付ける  
    <処理>  
  end  
end  

# OR  

class <Class>  
  class << self # まとめて書けるしメソッド名の修正も楽  
    def <method>  
      <処理>
    end 
  end  
end  
```  
## インスタンスメソッド  
インスタンスメソッドはレシーバーがインスタンス。  
つまりクラスの中のオブジェクト(=インスタンス)に対して使うメソッド。
`<object>.name``<object>.class`など。  
ドキュメントでは`Class#method`のような形で記載される。


# 継承  
`super`を使うと親クラスの同名メソッドを呼び出せる。  
親クラスの同名メソッドを呼び出して戻り値を返す。  
```  
class Product  
  def name  
    @name  
  end  
  def name=(text)  
    @name = text  
  end  
  def full_name  
    @name  
  end  
end  

class Manga < Product  
  def publisher  
    @publisher  
  end  
  def publisher=(text)  
    @publisher = text  
  end  
  def full_name  
    super # Product Classの@nameが返される  
  end  

manga = Manga.new  
manga.name = "ChainsawMan"  
manga.publisher = "Shueisha"  
puts manga.full_name #=> "ChainsawMan"  
```  

#privateメソッド  
インスタンスメソッドはそのクラス内でしかレシーバなしで呼び出せない。   
```  
class Yeah  
  def hi  
    "Hi!" + ho # 同クラスなのでレシーバがいらない  
  end  
  def ho  
    "Ho!"  
  end  
end  

yeah = Yeah.new  
p hi #=> undefined local variable or method `hi' for main:Object (NameError)  
p yeah.hi #=> "Hi!Ho!"  
# クラス外の場合はレシーバを指定しないとエラーになる   
```  
プライベートメソッドにすることでレシーバを指定してもクラス外からは使えない。  
```  
class Yeah  
  def hi  
    "Hi!" + ho # 同クラスなのでレシーバがいらない  
  end  
  
  private
    def ho  
      "Ho!"   
    end  
end  

yeah = Yeah.new  
p yeah.ho #=> private method `ho' called for #<Yeah:0x0000560167ee6240> (NoMethodError)  
p yeah.hi #=> "Hi!Ho!"  
```  
## 書き方  
private以降をすべてプライベートメソッドにするほかに、
ひとつひとつ指定することもできる。   
下記のように`def`の前に記述することで
パブリックなメソッドより前に記述することも可能。  
順番関係なくプライベートメソッドにすることができる。  
```  
private def <method>  
  <処理>  
end  

```  
## クラスメソッドをプライベートメソッドにする  
`private_class_method`と記載する必要がある。  
```  
class <Class>  
  private_class_method def self.<method>  
    <処理>  
  end  
end  
```  
ただし、クラスメソッドをまとめて書く`class << self`の場合は
インスタンスメソッドのように`private`を使用することができる。  
```  
class <Class>  
  class << self  
    private  
      def <method>  
        <処理>  
      end  
  end  
end  

# OR  

class <Class>  
  class << self  
    private def <method>  
        <処理>  
    end  
  end  
end  

```  
--20221021, 20221022  