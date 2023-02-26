# ストロングパラメータ

https://qiita.com/pop_man/items/5e930349f6a27a45bc3c  

https://diveintocode.jp/blogs/Technology/HTML3  

https://pikawaka.com/rails/strong_parameter  

https://qiita.com/P-man_Brown/items/9af0eaa8f3bccb3a33aa  

## 実際にやってみた
理解がいまいちなので実際に試してみた。
コードを試した時の状況説明付き。

### paramsを渡す
```
def create
  @user = User.new(params[:user])
  ~省略~
end
```
***結果***
```
ActiveModel::ForbiddenAttributesError (ActiveModel::ForbiddenAttributesError)
```
Railsによって、ストロングパラメータにしていないとこのエラーが出る。


### paramsを指定する
```
def create
  @user = User.new(email: params[:user][:email],
          password: params[:user][:password], name: params[:user][:name])
  ~省略~
end
```
***結果***
```
Started POST "/users" for 172.18.0.1 at 2023-02-26 14:38:03 +0900
Processing by UsersController#create as TURBO_STREAM
  Parameters: {"authenticity_token"=>"[FILTERED]", "user"=>{"email"=>"strong@strong.com", "password"=>"[FILTERED]", "password_confirmation"=>"[FILTERED]", "name"=>"strong"}, "commit"=>"Create User"}
  TRANSACTION (0.0ms)  begin transaction
  ↳ app/controllers/users_controller.rb:27:in `block in create'
  User Create (21.9ms)  INSERT INTO "users" ("email", "password_digest", "name", "created_at", "updated_at") VALUES (?, ?, ?, ?, ?)  [["email", "strong@strong.com"], ["password_digest", "[FILTERED]"], ["name", "strong"], ["created_at", "2023-02-26 05:38:03.464217"], ["updated_at", "2023-02-26 05:38:03.464217"]]
  ↳ app/controllers/users_controller.rb:27:in `block in create'
  TRANSACTION (9.8ms)  commit transaction
  ↳ app/controllers/users_controller.rb:27:in `block in create'
Redirected to http://localhost:3000/users/2
Completed 302 Found in 240ms (ActiveRecord: 31.8ms | Allocations: 3535
```
~~エラーは出ず、ユーザー作成できた。~~  
この時の自分はある誤解をしているのでこのように書いています。
誤解については後述します。  

#### キーを書き換える
ブラウザのデベロッパーツールを利用して
パラメータのキーを書き換える。
`user[email]`と`user[name]`を入れ替えた。
キー以外のフォームの属性やラベルの紐付けはそのまま。
***結果***
```
Started POST "/users" for 172.18.0.1 at 2023-02-26 15:54:10 +0900
Processing by UsersController#create as TURBO_STREAM
  Parameters: {"authenticity_token"=>"[FILTERED]", "user"=>{"name"=>"name@i", "password"=>"[FILTERED]", "password_confirmation"=>"[FILTERED]", "email"=>"strong@strong.com"}, "commit"=>"Create User"}
  TRANSACTION (0.0ms)  begin transaction
  ↳ app/controllers/users_controller.rb:27:in `block in create'
  User Create (17.4ms)  INSERT INTO "users" ("email", "password_digest", "name", "created_at", "updated_at") VALUES (?, ?, ?, ?, ?)  [["email", "strong@strong.com"], ["password_digest", "[FILTERED]"], ["name", "name@i"], ["created_at", "2023-02-26 06:54:11.086622"], ["updated_at", "2023-02-26 06:54:11.086622"]]
  ↳ app/controllers/users_controller.rb:27:in `block in create'
  TRANSACTION (7.9ms)  commit transaction
  ↳ app/controllers/users_controller.rb:27:in `block in create'
Redirected to http://localhost:3000/users/3
Completed 302 Found in 228ms (ActiveRecord: 25.3ms | Allocations: 2408)
```
いけちゃった。~~これではadminなどを書き換えられる可能性があり、危険。~~  
と思っていたがストロングパラメータありにしても同じことができた。
emailなのに@を含まないただの文字列を登録できた。これはバリデーションが足らないせいだと思う。  
この時点で誤解はまだ解けていない。

### ストロングパラメータ
```
def create
  @user = User.new(user_params)
  ~省略~
end
```
```
private
  def user_params
    params.require(:user).permit(:email, :password, :password_confirmation, :name)
  end
```
デベロッパーツールで`user[password_confirmation]`を`user[updated_at]`に書き換えた。

```
Started POST "/users" for 172.18.0.1 at 2023-02-26 16:24:04 +0900
Processing by UsersController#create as TURBO_STREAM
  Parameters: {"authenticity_token"=>"[FILTERED]", "user"=>{"email"=>"st1@strong.com", "password"=>"[FILTERED]", "updated_at"=>"2022", "name"=>"strong1"}, "commit"=>"Create User"}
Unpermitted parameter: :updated_at. Context: { controller: UsersController, action: create, request: #<ActionDispatch::Request:0x00007f45b6f9e1a8>, params: {"authenticity_token"=>"[FILTERED]", "user"=>{"email"=>"st1@strong.com", "password"=>"[FILTERED]", "updated_at"=>"2022", "name"=>"strong1"}, "commit"=>"Create User", "controller"=>"users", "action"=>"create"} }
  TRANSACTION (0.1ms)  begin transaction
  ↳ app/controllers/users_controller.rb:26:in `block in create'
  User Create (21.3ms)  INSERT INTO "users" ("email", "password_digest", "name", "created_at", "updated_at") VALUES (?, ?, ?, ?, ?)  [["email", "st1@strong.com"], ["password_digest", "[FILTERED]"], ["name", "strong1"], ["created_at", "2023-02-26 07:24:04.982531"], ["updated_at", "2023-02-26 07:24:04.982531"]]
  ↳ app/controllers/users_controller.rb:26:in `block in create'
  TRANSACTION (7.8ms)  commit transaction
  ↳ app/controllers/users_controller.rb:26:in `block in create'
Redirected to http://localhost:3000/users/5
Completed 302 Found in 230ms (ActiveRecord: 29.1ms | Allocations: 2453)
```
この時はうまく機能したな！と思ったけどそうではない。まだ誤解している。


## カラムを作った
usersテーブルにはカラムが少なくてストロングパラメータを学ぶには
不完全と感じたのでカラムを作成。
```
class AddColumnUsers < ActiveRecord::Migration[7.0]
  def change
    add_column :users, :admin, :integer, default: 0, null: false
    add_column :users, :strong, :boolean, default: false, null: false
  end
end
```
2つ用意したのは、フォームからtrue/falseと数値を送信できるのか試したかったから。
フォームから送ると文字列になりそうだなと。

### 試した
```
Started POST "/users" for 172.18.0.1 at 2023-02-26 16:47:09 +0900
Processing by UsersController#create as TURBO_STREAM
  Parameters: {"authenticity_token"=>"[FILTERED]", "user"=>{"email"=>"admin@admin.com", "password"=>"[FILTERED]", "admin"=>"1", "name"=>"admin"}, "commit"=>"Create User"}
  TRANSACTION (0.1ms)  begin transaction
  ↳ app/controllers/users_controller.rb:27:in `block in create'
  User Create (32.7ms)  INSERT INTO "users" ("email", "password_digest", "name", "created_at", "updated_at") VALUES (?, ?, ?, ?, ?)  [["email", "admin@admin.com"], ["password_digest", "[FILTERED]"], ["name", "admin"], ["created_at", "2023-02-26 07:47:10.108739"], ["updated_at", "2023-02-26 07:47:10.108739"]]
  ↳ app/controllers/users_controller.rb:27:in `block in create'
  TRANSACTION (8.8ms)  commit transaction
  ↳ app/controllers/users_controller.rb:27:in `block in create'
Redirected to http://localhost:3000/users/8
Completed 302 Found in 247ms (ActiveRecord: 41.5ms | Allocations: 2575)
```
ここでやっと、DBにカラムがあるのに入力したデータが弾かれていることに気がつく。  
paramsではこれ↓
```
Parameters: {"authenticity_token"=>"[FILTERED]", "user"=>{"email"=>"admin@admin.com", "password"=>"[FILTERED]", "admin"=>"1", "name"=>"admin"}, "commit"=>"Create User"}
```
ブラウザからキーを書き換えて送信した`"admin"=>"1"`がある。  

クエリになると下記のように`"admin"=>"1"`がなくなる。  
```
INSERT INTO "users" ("email", "password_digest", "name", "created_at", "updated_at") VALUES (?, ?, ?, ?, ?)  [["email", "admin@admin.com"], ["password_digest", "[FILTERED]"], ["name", "admin"], ["created_at", "2023-02-26 07:47:10.108739"], ["updated_at", "2023-02-26 07:47:10.108739"]]
```
これはおかしいぞ〜と思い、次へ。

## 必要なケース・必要ないケース
受け取るパラメータを指定する場合、ストロングパラメータは必要ない。
しかし、マスアサインメント機能ではある。  
### ストロングパラメータが必要ない場合
```
User.new(email: params[:user][:email],
          password: params[:user][:password], name: params[:user][:name])
```
### ストロングパラメータが必要ある場合
```
User.new(params[:user])
# 現在のRailsはこの書き方をするとエラーが出る仕様
```
## ストロングパラメータが必要ない書き方でずっと試してた
先述の誤解とはこのこと。
必要ない方法で試しているので改ざんされずにユーザー登録ができるのは当たり前のことかもしれない。
知らなかった。


## DBにカラムがないデータは保存されない
カラムのないデータは保存されない。**多分。**

### 存在しないカラム`wow`をストロングパラメータのキーに追加して試した。
```
private
  def user_params
    params.require(:user).permit(:email, :password, :password_confirmation, :name, :wow)
  end
```
デベロッパーツールで`user[password_confirmation]`を`user[wow]`に書き換えた。
submitすると下記のエラーに。
```
ActiveModel::UnknownAttributeError in UsersController#create
unknown attribute 'wow' for User.
```
エラー箇所はcreateアクションの`@user = User.new(user_params)`。  

### 存在しないカラム`wow`をアクションでparamsのキーに追加して試した。
```
@user = User.new(wow: params[:user][:wow], email: params[:user][:email], password: params[:user][:password], name: params[:user][:name])
```
デベロッパーツールで`user[password_confirmation]`を`user[wow]`に書き換えた。
submitすると下記のエラーに。
```
ActiveModel::UnknownAttributeError in UsersController#create
unknown attribute 'wow' for User.
```
二つのエラーは同じだった。  
存在しないカラムを存在するかのように扱うとタイポの時と似たような感じになる。  

ブラウザでキーを存在しないカラム名に書き換えた状態で
1. パラメータをそのまま渡すとエラーになる
2. ストロングパラメータに追加するとエラーになる
3. アクション側でparamsのキーに追加するとエラーになる
存在しないカラムをDBに保存することができるかはわからない。

---
# 番外編
せっかくadminカラムとstrongカラムを作ったので。
フォームからboolean型、integer型は送れるのか。
調べ方が悪いのか調べても出てこない。  
多分テキストフィールドなどの文字列を送るフォームタグからはboolean型、integer型は送れない。
調べた感じJSONを使ったり受け取る側でいじってあげればその限りではない。  



--20230226