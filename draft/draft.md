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
