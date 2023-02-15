
gem install -v 5.2.6 rails

P101 3-3#1-2はskip

P109 

４章までやる　５章以降はいったん飛ばす

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

userがnil
createしてもrendernewされてるから作れてなさそう

binding.pry
@user
=> #<User:0x00007fdaa8943f38
 id: nil,
 name: "passpass",
 email: "pass@pass.com",
 password_digest: "[FILTERED]",
 admin: false,
 created_at: nil,
 updated_at: nil>

--1231



IDとViewの不一致

end忘れたときの×が出ないー＞インスタンスの停止、起動で治った

redirect_to question_path(@question), success: '質問を作成しました'
        # flash[:success] = '質問を作成しました'　でも良い。
        # redirect_toの第二引数にできるflashのキーはデフォルトで決められているので
        # application_controllerにadd_flash_types :success, :info, :warning, :dangerを追加
        # successを使えるようにした


問題

URLのIDを何にしても/questions/:id  の内容がid:1のquestionになってしまう。
サーバー再起動済み。
/questions/:id/editは正常。
編集後のリダイレクトでは上記の問題が起こる。
直リンも同様なのでeditアクションではなく
showアクションかshow.html.erbあたりの問題か。
おそらく@questionの中身がうまく動いていない。
routesを間違えた？
=> Question.findをQuestion.find_byにしていた。
  findはデータを複数取得できます。
  find_byは最初にマッチした1件のみ取得できます。
  とあるように最初の1件しか取得できなかったので
  id:1のものしか表示されなかった。
  

●7分あたりのform_withのモデルの説明きく
answerを作るフォームでは、form_withのmodel部分に
配列形式でquestionの情報を与える必要がある。
answerはquestionありきのものとして実装しているため、
form_withが自動生成するformタグのURLがうまく作られない。  

●11分あたりのcreateアクションのコード説明きく
answersコントローラのcreateアクションにて。
```
@answer = current_user.answers.build(answer_params)
# 上記だとquestionの情報を拾えていないので下記が必要
@answer.question_id = params[:question_id]
```
↑だと2つのコードが必要
```
@answer = current_user.answers.build(
      answer_params.merge(question_id: params[:question_id]))
```
このようにして1つのコードにすることができる。
ハッシュをマージしている。
`answer_params`アクションの戻り値になっているハッシュに
`question_id`のハッシュを追加している。多分。

●55分あたりの解決済みにするボタン


検索機能にransack便利

https://qiita.com/hirokihello/items/fa82863ab10a3052d2ff
resourcesにcollectionをネストする
resourcesで自動生成されるもの以外のルーティングを指定したいときに。
:idが必要なルーティングを指定するときはmember
必要ないときはcollection

https://qiita.com/nakachan1994/items/72f0fd1cf8193cca8188
No Ransack::Search object was provided to search_form_for!
というArgumentErrorが出た
before_actionにして解消

55分経過

解決済みにするボタンまわりでエラー

```
ActiveRecord::RecordNotFound in QuestionsController#solve
Couldn't find Question with 'id'=1 [WHERE "questions"."user_id" = ?]
```
```
def solve 
    @question = current_user.questions.find(params[:id])
    @question.update!(solved: true)
    redirect_to question_path(@question), success: '解決済みにしました'
  end
```
paramsのとこ間違えてたので修正
```
ActiveRecord::RecordNotFound in QuestionsController#solve
Couldn't find Question without an ID
```
```
  def solve 
    @question = current_user.questions.find(params[:question_id])
    @question.update!(solved: true)
    redirect_to question_path(@question), success: '解決済みにしました'
  end
```
IDのないquestionを探しに行っちゃったらしい
ルーティング確認
```
solve_question POST   /questions/:id/solve(.:format) questions#solve
```
コード間違えてない？
そもそもこのparamsって何をさしてる？
[WHERE "questions"."user_id" = ?]これなに？
書き直したらいけたなぜか

enumとは


ActiveRecord::RecordNotFound in QuestionsController#show
Couldn't find Question with 'id'=users
  def show
    @question = Question.find(params[:id])
  end
プレビューのリンクを打ち間違えていたわら

indexページのレンダリングはeach文ではなくパーシャルを作った方が
パフォーマンスも良い
```
<% @users.each do |user| %>
  <%= user.name %>
<% end %>
```
これを変える
`_user.html.erb`のようにモデル名（単数）で名前づけ
```
<%= user.name %>
# ここの変数も単数
```
```
index.html.erb
  <%= render @users %>
  # ここは複数に
```

adminLTEというフレームワーク使うと管理画面いい感じに作れる



$ yarn add admin-lte@^3.2
yarn add v1.22.19
warning ../../../package.json: No license field
[1/4] Resolving packages...
warning admin-lte > flag-icon-css@4.1.7: The project has been renamed to flag-icons
warning admin-lte > popper.js@1.16.1: You can find the new Popper v2 at @popperjs/core, this package is dedicated to the legacy v1
warning admin-lte > bootstrap-colorpicker > popper.js@1.16.1: You can find the new Popper v2 at @popperjs/core, this package is dedicated to the legacy v1
warning admin-lte > tempusdominus-bootstrap-4 > popper.js@1.16.1: You can find the new Popper v2 at @popperjs/core, this package is dedicated to the legacy v1
warning admin-lte > pdfmake > @foliojs-fork/linebreak > brfs > static-module > magic-string > sourcemap-codec@1.4.8: Please use @jridgewell/sourcemap-codec instead
[2/4] Fetching packages...
[3/4] Linking dependencies...
warning "admin-lte > bootstrap-switch@3.3.4" has incorrect peer dependency "bootstrap@^3.1.1".
warning "admin-lte > tempusdominus-bootstrap-4@5.39.2" has unmet peer dependency "moment-timezone@^0.5.31".
warning "admin-lte > tempusdominus-bootstrap-4@5.39.2" has unmet peer dependency "tempusdominus-core@5.19.3".
[4/4] Building fresh packages...
success Saved lockfile.
success Saved 126 new dependencies.
info Direct dependencies
└─ admin-lte@3.2.0
info All dependencies
以下略

@popperjs/core で新しい Popper v2 を見つけることができます。このパッケージはレガシー v1 専用です。


管理画面作り
ルーティング
```
namespace :admin do
  resources :users, only: [:index]
end
```
コントローラ
```
rails g controller admin/users
```
管理画面に共通する処理をまとめるコントローラ
```
rails g controller admin/base
```
base以外のadminコントローラは継承をAdmin::Baseに変える
```
class Admin::UsersController < ApplicationController
end
↓
class Admin::UsersController < Admin::BaseController
end
```
adminの共通ビュー設定を作る
1. `views/admin/layouts`を作る
2. その中に`application.html.erb`を作る
3. もう一つの`application.html.erb`の中身を一旦コピペする
4. 管理画面とわかる文字を表示させる用に編集する
4. `base_controller.rb`に`layout 'admin/layouts/application'`と記載する
5. 反映されているか確認
6. 管理画面用に編集する

adminLTE yarnでも入れたしCDNでも入れてる？片方で良いのかな
yarnで入れたの消す
$ yarn remove adminLTE
yarn remove v1.22.19
warning ../../../package.json: No license field
[1/2] Removing module adminLTE...
error This module isn't specified in a package.json file.

そもそも入ってないこともあるとのこと
https://mebee.info/2021/09/29/post-32224/

install打つ時のスペルを確認して挑戦
$ yarn remove admin-lte
yarn remove v1.22.19
warning ../../../package.json: No license field
[1/2] Removing module admin-lte...
[2/2] Regenerating lockfile and installing missing dependencies...
success Uninstalled packages.
Done in 8.71s.


link_toがうまく機能しない。動画50分あたり
confirmも出ないしメソッドもGETになっちゃう。
UJSが読み込めてないらしい
```
<%= csrf_meta_tags %>
<%= csp_meta_tag %>

<%= stylesheet_link_tag 'application', media: 'all', 'data-turbolinks-track': 'reload' %>
<%= javascript_pack_tag 'application', 'data-turbolinks-track': 'reload' %>

```
これらが`admin/application.html.erb`にはなかったので、
adminではない`application.html.erb`からコピペする。
# assetを分ける
管理画面とそうでない画面でassetを違うものにした方が良い。
## リンクタグ書き換え
`admin/application.html.erb`内、
リンクタグの参照が`application`だと管理画面以外のページと同じもののため
バッティングする可能性がある。書き換える。
```
<%= stylesheet_link_tag 'admin/application', media: 'all', 'data-turbolinks-track': 'reload' %>
```
## リンクタグのassetを作る
`app/assets/stylesheets/admin`に`application.scss`を作る。
## コンパイルのため明示する
自分で作ったcssはコンパイルしてくれないので明示する。
`config/initializers/assets.rb` 最後の行コメントアウトを解除して編集
scssでもここの記載はcssにしないとプリコンパイルエラーになる
```
Rails.application.config.assets.precompile += %w( admin/application.css )
```
## パックタグ書き換え
パックタグの参照も同様にバッティングを避ける。書き換える。
```
<%= javascript_pack_tag 'admin/application', 'data-turbolinks-track': 'reload' %>
```
## パックタグのassetを作る
`javascript/packs/admin/application.js`を作る。
`packs/application.js`の内容をコピペ。
## 確認
開発者ツールでheadタグ内を見る
```
<link rel="stylesheet" media="all" href="/assets/admin/application.debug-bfc(省略).css" data-turbolinks-track="reload">
<script src="/packs/js/admin/application-27bc614c1a515db502f3.js" data-turbolinks-track="reload"></script>
```
それぞれadminを参照できていることが確認できる。
コンパイルされたあとのファイルは`public/packs/js`内に保存される。
railsはここにあるファイルを読み込んでいる。

ノンデザイナーズデザインブック

管理画面ログインページ
ログイン前なのにサイドバーが表示されている
* ログイン画面用のレイアウトファイルを作る
* レイアウトファイルを使わない
どちらかで対処する
# レイアウトファイル(application.html.erb)を使わない場合
## admin/sessions_controllerに記載
```
layout false
```
### ビューファイルにテンプレートを流し込む
`admin/sessions/new.html.erb`はadminLTEのログインページ用を
コピペした。
## headタグをコピペする
`admin/application.html.erb`のheadタグ内、
linkタグやscriptタグをコピーして
`admin/sessions/new.html.erb`の同じ部分に置き換える

# placeholder
フォームに入ってる薄い文字のこと
フォームタグなら`placeholder="Email`、
form_withなら`placeholder: 'Email'`


起きてる問題
ログインしている状態で新しいユーザーを作ったら
リダイレクトがUsers#new
flashは新しいユーザー名
ヘッダーのログイン名は前のユーザー
def require_admin
  redirect_to root_path unless current_user.admin?
end
未ログイン状態で/admin/loginにアクセスすると
current_userがnilのためエラーになる
管理画面のログインフォームが正常に機能していない。
パスワード、メアドあっているのにログイン画面にリダイレクトする。
管理者が普通のログイン状態を保持したまま/admin/users等にアクセスかのう。
管理者ログインせず。
userはnilになってしまうパスワードが違うのか？なんだろう
form_with内、inputタグのname属性になる部分が誤っていた。
<%= f.password_field :email, class: 'form-control', placeholder: 'Password' %>
になっていて、パスワードなのにemailとなっていた。コピペ後の直し忘れ。
password_fieldに入力した方のemailからfind_byしていたのか、
２つのemailでfind_byしていたのかはわからない。

管理者ログアウトするボタンないが、
検証ツールからcookieを削除すると
セッションが消される。
セッションは設定をいじっていないからcookieに保存されている。
検証ツール/application/cookie
cloud9はAWSのクッキーも消えてサーバー終了してしまうので
それだと思うのを一つ選んで消す。なんちゃら_sessionというやつ
ローカル環境なら全部消してもOK

未解決、解決のそれぞれで検索を掛けられるようにしたい
今は検索しても全てになってしまう
solved actionでsolved: trueをransackの検索フォームにセットしたい
form_withにurl: request.pathを追加し動いた

requestとは？


An error occurred while loading ./spec/views/sessions/new.html.erb_spec.rb.
Failure/Error: config.include FactoryBot::Syntax::Methods

NameError:
  uninitialized constant FactoryBot
# ./spec/rails_helper.rb:64:in `block in <main>'
# ./spec/rails_helper.rb:33:in `<main>'

https://qiita.com/aoi1019m/items/5e5701ba05629e2367a8
gemfile内の`gem 'factory_bot_rails'`を
`group :development, :test do`の中に移動させる


rspec
仕様書のように書ける
現場Rails5章を読んで
テストケースを整理・分類する：describe, context
テストコードを実行する：before, it
## describe
contextはdescribeのエイリアスなので、どちらを使っても同じように動作する
beforeはitが実行されるたびに新たに実行される
だからあるテストケースのせいで別のテストケースが影響を受けることは基本ない

contextで場合分けする


describeはネストすることもあり、見出しを作るイメージ
大外はdescribe

answers_ctrlとquestions_ctrlのメイラー


scope :related_to_question, ->(question) 
        { joins(:answers).where(answers: { question_id: question.id }) }
使用例
User.related_to_question(@answer.question)
愚直に書くと
User.joins(:answers).where(answers: { question_id: @question.id })

UserにanswersテーブルをJOINする。
どんなデータを？→
User.answersは、answersテーブルを結合する。
where(answers: { question_id: @question.id })は、
@questionのIDが解答のquestionIDと同じである解答を探す


環境構築やる
無変換もしくは変換取り消しやり方
最小化最大化
画面の分割
選択もう一回押すのやめたい
Docker


Docker説明
https://qiita.com/k5n/items/2212b87feac5ebc33ecb