

# mount_procメソッド  
https://lemniscus.hatenablog.com/entry/20090722/1248261257

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


