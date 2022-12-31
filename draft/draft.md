
gem install -v 5.2.6 rails

P101 3-3#1-2はskip

P109 

４章までやる　５章以降はいったん飛ばす

無理してフロントとバックエンドを分けるのはめちゃくちゃ大変だからむりせず
ポートフォリオの話

---

--1127

RESTfulなルーティングの話
POST /posts　は新規登録の時だけ　IDがまだないから
IDの付与はただ登録された順番 削除されて歯抜けになっても
新しいレコードはそこに入り込まない


byebug
binding.pry
処理を止めたいときは入れる
止まらなかったときは仕込む場所が違う （処理の道としてそこを踏んでいない）
変なところ（コールバックなど）にいったら一回終わらせて
手動で仕込む場所をずらしてみる

--221204

プルリクを作ったあとにマージ先を変えられる
github project isssue管理

HTTP verb
HTTPリクエストメソッドのこと
GET, POST, PUT, PATCH, DELETE



# 実装編
1. ~ユーザー認証
 現場railsの4-5
Userモデルを作る
新規作成ページを作る

2. 


$ rails -v
  Warning: the running version of Bundler (2.1.4) is older than the version that created the lockfile (2.2.16). We suggest you to upgrade to the version that created the lockfile by running `gem install bundler:2.2.16`.
  The dependency tzinfo-data (>= 0) will be unused by any of the platforms Bundler is installing for. Bundler is installing for ruby, x86_64-darwin-19 but the dependency is only for x86-mingw32, x86-mswin32, x64-mingw32, java. To add those platforms to the bundle, run `bundle lock --add-platform x86-mingw32 x86-mswin32 x64-mingw32 java`.
  Rails 6.1.3.1
$ gem install bundler:2.2.16
  Fetching bundler-2.2.16.gem
  Successfully installed bundler-2.2.16
  Parsing documentation for bundler-2.2.16
  Installing ri documentation for bundler-2.2.16
  Done installing documentation for bundler after 3 seconds
  1 gem installed
$ rails -v           
  Resolving dependencies...
  Unable to find a spec satisfying nokogiri (~> 1.8) in the set. Perhaps the lockfile is corrupted? Found nokogiri (1.11.3-x86_64-darwin) that did not match the current platform.
$ gem install bundler:2.1.4
  Fetching bundler-2.1.4.gemSuccessfully installed bundler-2.1.4
  Parsing documentation for bundler-2.1.4
  Installing ri documentation for bundler-2.1.4
  Done installing documentation for bundler after 3 seconds
  1 gem installed
$ rails -v
  Resolving dependencies...
  Unable to find a spec satisfying nokogiri (~> 1.8) in the set. Perhaps the lockfile is corrupted? Found nokogiri (1.11.3-x86_64-darwin) that did not match the current platform.Run `bundle install` to install missing gems.
$ git reset --hard
  HEAD is now at cc9f056 add rspec
$ rails -v
  Resolving dependencies...
  Unable to find a spec satisfying nokogiri (~> 1.8) in the set. Perhaps the lockfile is corrupted? Found nokogiri (1.11.3-x86_64-darwin) that did not match the current platform.
  Run `bundle install` to install missing gems.
  
実行中の Bundler のバージョン (2.1.4) は、ロックファイルを作成したバージョン (2.2.16) より古いです。 
`gem install bundler:2.2.16` を実行して、ロックファイルを作成したバージョンにアップグレードすることをお勧めします。

nokogiriのバージョン要件に満たない？
セット内にノコギリ(~>1.8)を満たすスペックが見つかりません。
lockfile壊れてませんか？nokogiri (1.11.3-x86_64-darwin)と書いてありますよ～とのこと。


nokogiriとは
スクレイピング（Webサイトから情報を抽出する）をする際に利用されるもの
https://qiita.com/yuki82511988/items/e73224f551cb80dab2f1

bundle updateしたら治った
https://qiita.com/hayatoganbaru/items/1fc5da371f7762b33ebd

-221211

マイグレーションしたらコンソールで動作確認
pecoというライブラリはルーティング絞り込めて便利


LoadError in UsersController#new
cannot load such file -- bcrypt
Extracted source (around line #2):
         
class User < ApplicationRecord
  has_secure_password
  
end

サーバー再起動で解決
https://nanairo-taiyou.com/rails_error_bcrypt20200420/


名前付きパスを確認する方法
railsconsoleで
app.名前付きパス


46分まで見た

--1231