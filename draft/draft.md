
while条件を満たすまで繰り返す

# 配列
`array.pop` で末尾削除  
`array.shift` で先頭削除  
`array.push(object)` で末尾追加  
`array.unshift(object)` で先頭追加  

# break
each文の処理を途中で終わらせる  
```  
array = [1,2,3,4,5]  
array.each do |i|  
  break if i == 3  
  puts i  
end  
breakの後の条件を満たす場合  
このeach文のブロック自体を終了する  
>>1  
2  
```  

# next  
each文の処理を途中にして先に進める  
```
array = [1,2,3,4,5]
array.each do |i|
  next if i == 3
  puts i
end
nextの後の条件を満たす場合  
そのオブジェクトの処理をそこで終わらせて  
次のオブジェクトの処理に移る  
>>1
2
4
5
```  

# uniqメソッド  
配列から重複した要素を取り除いた新しい配列を作る  
```  
array1 = [1, 3, 7, 5, 5, 1]  
array2 = array1.uniq  
p array1 #=> [1, 3, 7, 5, 5, 1]  
p array2 #=> [1, 3, 5, 7]  
```  
重複しない新しい配列を作るので元の配列が書き換わるわけではない。  

書き換えたい場合はuniq!を使用  
削除した場合はself そうでなければnilを返す
```  
array1 = [1, 3, 7, 5, 5, 1]  
array2 = array1.uniq!  
p array1 #=> [1, 3, 5, 7]  
p array2 #=> [1, 3, 5, 7]  
```  
自身を書き換えるので破壊的変更  
オブジェクトidというオブジェクトごとの識別idを用いて破壊的かどうか検証できる。  
```
p array1.object_id #=> (同じオブジェクトid)  
p array2.object_id #=> (同じオブジェクトid)  
```  

-20221017, 20221019

# sort  
昇順に並び替えるメソッド  
数値なら小さい順、文字列ならアルファベット順  
大文字と小文字がある場合 大文字が先になる aよりZの方が先になる  
降順にしたい場合はreverseメソッドを併用  
```  
array = [3, 5, 1, 7]
array.sort #=> [1, 3, 5, 7]
array.sort.reverse #=> [7, 5, 3, 1]

array2 = [haha, Umm, Ah, oh, Huh]   
array2.sort #=> [Ah, Huh, Umm, haha, oh]  
array2.sort.reverse #=> [oh, haha, Umm, Huh, Ah]  
```   
reverseはソートではなく文字列を逆順にもできる  
```  
"reverse".reverse #=> "esrever"  
```  

--

# map  
配列の要素ひとつずつに処理をして新しい配列を作る  
```  
result = [1, 2, 3].map do |x|  
  x * 2  
end  
p result  

>>
[2, 4, 6]
```  
```  
result = [100, 200, 300].map do |x|  
  "#{x}円"  
end  
p result  

>>  
["100円", "200円", "300円"]  
```  

## 2つのhashをひとつにまとめる  
```  
coffee_menu = {coffee: 300, caffe_latte: 400}  
tea_menu = {tea: 300, tea_latte: 400}  
menu = coffee_menu.merge(tea_menu)  
p menu  

>>  
{:coffee=>300, :caffe_latte=>400, :tea=>300, :tea_latte=>400}  
```  

--1020

# 変数のスコープ  

変数にはスコープがある。  
スコープとは見える範囲と寿命のこと。認識される範囲。  
メソッド内で定義したローカル変数は定義したメソッドの中がスコープ。
メソッドの外で使えない。
メソッド外で定義したローカル変数はメソッド外がスコープ。
メソッドの中で使えない。  
スコープをメソッドの内外に広げたい場合はインスタンス変数を使用する。  
@のやつ。オブジェクトが持つ変数なので**インスタンス変数**。  

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

--1021  

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

# ライブラリ  
1. 組み込みライブラリ(準備不要)  
2. 標準添付ライブラリ(`require`すると使える)  
3. Gem(インストール必要)  

# Gemfile  
Gemfileは注文書でGemfile.lockは納品書。  
## 前に使用したバージョンを使いたい場合  
新しいバージョンのgemをインストールしたとき
古いバージョンはアンインストールされない。  
新しいバージョンが使用されるが、
過去にインストールした古いバージョンを使用したい場合は
`bundle exec`する。  
Gemfile.lockに書かれたバージョンでプログラムを実行できる。  


--1022

gem install -v 5.2.6 rails

P101 3-3#1-2はskip

P109 
.から始まったらdiv divがうるさいので　それ以外は明記されている
クラス名の後ろ=がくっついていたら#{}か<%= %>
文頭の=は<%= %>
文頭の-は<% %>


４章までやる　５章以降はいったん飛ばす

無理してフロントとバックエンドを分けるのはめちゃくちゃ大変だからむりせず
ポートフォリオの話

--1113

マイグレーションはデータベースごとに適用する必要がある
オプションなしだと開発環境のみ
本番環境用
$ rails db:migrate RAILS_ENV=production
テスト用
$ rails db:migrate RAILS_ENV=test

schema.rb
現在のデータベース構造が自動的に出力されているファイル

ノーマルのmigrate以外
バージョンを指定してもそのマイグレーションだけが適用されるのではなく
その時点のマイグレーションが適用される。
$ rails db:migrate VERSION=YYYYMMDDHHMMSS
指定したバージョンまでのマイグレーションが適用される
$ rails db:migrate:redo
バージョンを戻して上げるという動作を一気に行う。STEPで指定可能。  
結果としては通常のマイグレートと一緒。  
新しいマイグレーションファイルを作らなくてもいいか～というときの
ショートカットとして使える。  
その場合既に作られたマイグレーションファイルに書き込みredoする。
$ bin/rails db:rollback STEP=n
現在のマイグレーションから戻す。デフォルトは1
STEPでいくつのマイグレーションを戻すのか指定


--1114