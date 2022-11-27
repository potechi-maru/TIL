# モジュール 
細かな部品が合わさってできた部品。 
ひとまとまりの機能。 
自転車の車輪、電源プラグなど。インターホンは家のモジュール。 
ライブラリと違い、モジュール単品でも一応機能するとのこと。 

# モジュール  
さまざまなクラスで使える共用メソッド定義場所  
クラスのように定義するがインスタンスは作れない。
(`<Module>.new`はできない)  
`include`することでクラス自身の
インスタンスメソッドのように使用できる。  
クラスメソッドとして使いたい場合は、
`extend`する。
継承は「子クラスは親クラスの一種である」
という関係でないと違和感があるので
そうでないけどクラスをまたいで
同じメソッドを使いたいときに使うと良い。  

## インスタンスメソッドとして使いたい場合  
```  
module WhippedCream  
  def whipped_cream  
    @name += "ホイップクリーム"  
  end  
end  

class Drink  
  include WhippedCream  
  def initialize(name) # newすると自動で実行される  
    @name = name  
  end  
  def name  
    @name  
  end  
end  

drink = Drink.new("ココア")  
drink.whipped_cream  
puts drink.name #=> ココアホイップクリーム  
```  
## クラスメソッドとして使いたい場合  
```  
module Greeting  
  def welcome  
    "いらっしゃいませ"  
  end  
end  

class Cafe  
  extend Greeting  
end  

puts Cafe.welcome #=> "いらっしゃいませ"  
```  

## モジュールで自身のクラスメソッドのようなものを作る  
クラスメソッドのように、
モジュール自身のメソッドを作ることができる。  
```  
module WhippedCream  
  def self.info # クラスメソッドのようにselfを使う  
    "トッピング用ホイップクリーム"  
  end  
end  

puts WhippedCream.info #=> トッピング用ホイップクリーム  
```  

## 定数を使う  
```  
module WhippedCream  
  Price = 100  
end  

puts WhippedCream::Price #=> 100  
```  

## 名前空間  
別々のクラスに同じクラス名を使いたい場合に、
モジュール(またはクラス)を使うことで可能になる。  
インスタンスを作らない場合はモジュールが適切。  
作る場合はクラスを使用する。  
`<Class>::<Module>`や`<Module>::<Class>`など、
クラス(モジュール)の間を`::`で繋ぐことで
同じ名前でも使い分けることができる。  
```  
module HelloCafe  
  class Coffee  
    def self.info  
      "まろやかなコーヒー"  
    end  
  end  
end  

module BonjourCafe  
  class Coffee  
    def self.info  
      "渋いコーヒー"  
    end  
  end  
end  

puts HelloCafe::Coffee.info #=> "まろやかなコーヒー"  
puts BonjourCafe::Coffee.info #=> "渋いコーヒー"  

```  


# 別のファイルからモジュールを読み込む  
同じファイルではなく別のファイルに定義した
モジュールを使うときは
`require_relative`する必要がある。  
読込元ファイルと読込先ファイルの
親ディレクトリが同じであれば
`require`でもOK。`require "./<filename>"`
`include`はモジュールに書かれたメソッドを
クラスで使うための記載で、
`require_relative`または`require`は
別のファイルの内容を読み込むための記載。  
```ruby:whipped_cream.rb  
module WhippedCream  
  def whipped_cream  
    @name += " add whipped cream"  
  end  
end  
```  
```ruby:donuts.rb  
require_relative "whipped_cream" # or require "./whipped_cream"  
class Donuts  
  include WhippedCream  
  
  def initialize(name)  
    @name = name  
    puts "This is the #{@name} donuts!"  
  end  
  
  def name  
    @name  
  end  
end  

donut1 = Donuts.new("chocolat")  
donut1.whipped_cream  
puts donut1.name  

```  

-20220913, 20221022