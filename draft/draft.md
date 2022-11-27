
gem install -v 5.2.6 rails

P101 3-3#1-2はskip

P109 

４章までやる　５章以降はいったん飛ばす

無理してフロントとバックエンドを分けるのはめちゃくちゃ大変だからむりせず
ポートフォリオの話

---

ログインログアウト機能がある
ユーザーはニックネームとアバター画像を登録できる
ユーザーは質問を投稿できる
ユーザーは自分の質問を編集・削除できる
ユーザーは質問に対して回答ができる
ユーザーは質問を解決済み状態に変更できる
ユーザーは質問を検索できる
質問があった際に全員に対して質問があった旨をメールで通知する（ただし自分は除く）
質問に対して回答があった場合は質問者および当該質問に回答したユーザーに対してメールで通知する。（ただし自分は除く）
質問はページングできる
管理画面がある
管理画面へは権限を付与されたユーザーしか入れない
管理画面では全てのリソースを削除できる

~
User has_many :question, :answer
Question belongs :user
  hasmany :answer
Answer belongs :user
* user
  * name:string: 
  * email:string
  * password_digest:string
  * remember_digest:string
  * abatarphoto
  * created_at:datetime
  * updated_at:datetime
  * admin:boolean
  * 
* question
  * title:string
  * content:text
  * solved:boolean
  * user_id:integer
  * created_at:datetime
  * updated_at:datetime
* answer
  * content:text
  * user_id:integer
  * question_id:integer
  * created_at:datetime
  * updated_at:datetime