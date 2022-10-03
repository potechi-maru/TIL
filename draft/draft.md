1001, 1002

# mount_procメソッド  
https://lemniscus.hatenablog.com/entry/20090722/1248261257
https://qiita.com/kure/items/eb91c770913f59cf8708

```webrick.rb
server.mount_proc(dir) {|req, res|
  # 指定したい動き
}
```  
第一引数にマウントするディレクトリを指定  
reqはリクエスト、resはレスポンス  

# マウントとは  
https://wa3.i-3-i.info/word13188.html
接続したものが使用できることを認識させること。  
PATHを通すことに似てるかも。  

# メモ  
erbにするなら拡張子はhtml.erbである必要があると思う。
レスポンスボディはHTMLだから最終的にHTMLに変換されているので
その最終的な動作をwebrick.rbにかければ良いのでは？


You may be using the wrong PORT & IP for your server application.For rails, use: 'rails s -p 8080'. For Sinatra, use: 'ruby app.rb -p 8080'.
とでたのでwebrick.rbのポート番号を一瞬変えてみた　すぐ戻した

サーバーにアクセスしてもルートすらNotFoundになってしまう
多分ポート番号の変更が悪かった？

https://www-creators.com/archives/1290#_git_add
`git checkout HEAD webrick.rb`した
やっぱりルートすらNotFound


server.mount_proc("/time") do |req, res|
  # レスポンス内容を出力
  body = "<html><body>\n"
  body += "#{Time.new}"
  body += "</body></html>\n"
  res.status = 200
  res['Content-Type'] = 'text/html'
  res.body = body
end

---  

https://teratail.com/questions/66016


以下1003

# Gitとは  
## Gitとは  
ソースコードをバージョン管理するシステム。
## Gitがないと  
* チーム開発の際にメンバーそれぞれで同一ファイルを編集するため、
ひとつのファイルから複数のファイルが生まれることで
ひとつに統合する手間があったり、内容に齟齬が生まれたりする。
それが原因でエラーが起きることもある。  
* 変更を加えてエラーが起きてしまったとき、
過去のある時点のソースコードに戻れない。  
## ブランチとは  
本番のソースコードを複製したもの。
ブランチを作って編集し、問題が起こらないか確認したうえで
本番のコードに差し替えることができる。
そのため、ユーザーが見る画面に突然エラーが出たり、
意図しない挙動になることを防ぐことができる。  
