
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
| やりたいこと | HTTPメソッド | エンドポイント | コントローラ#アクション |
| --- | --- | --- | --- |
| ユーザー登録画面を表示する | GET | /users/new | users#new |
| ユーザー登録をする | POST | /users/new | users#create |
| ログイン画面を表示する | GET | /users/login | users#login |
| ログインする | POST | /users/login | sessions#new |
| ログアウトする | DELETE | /users/logout | sessions#destroy |
| 質問一覧を表示する（全て） | GET | /questions | questions#index |
| 質問一覧を表示する（未解決） | GET | /questions/unsolved | questions#unsolved |
| 質問一覧を表示する（解決済み） | GET | /questions/solved | questions#solved |
| 質問投稿ページを表示する | GET | /questions/new | questions#new |
| 質問投稿をする | POST | /questions/new | questions#create |
| 質問詳細を表示する | GET | /questions/:id | questions#show |
| 質問編集ページを表示する | GET | /questions/edit | questions#edit |
| 質問を削除する | DELETE | /questions/delete | questions#destroy |
| 回答する | POST | /questions/:id/answer/new | answers#new |
| ユーザー一覧を表示する | GET | /users | users#index |
| 管理画面用のログインページを表示する | GET | /admin/users/login | Admin::sessions#new |
| 管理画面用のログインをする | POST | /admin/users/login | Admin::sessions#create |
| （管理画面）質問一覧ページを表示する | GET | /admin/questions | Admin::questions#index |
| （管理画面）質問を削除する | DELETE | /admin/questions/delete | Admin::questions#destroy |
| （管理画面）ユーザー一覧ページを表示する | GET | /admin/users | Admin::users#index |
| （管理画面）ユーザーを削除する | DELETE | /admin/users/:id/delete | Admin::users#destroy |

adminのログイン画面が必要
/view/users/admin/login.html.erb かな
