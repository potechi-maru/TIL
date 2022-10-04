# WEBrick  
単純なHTTPwebサーバー機能Rubyのライブラリのひとつ。 
Ruby3.0で削除されたため、3.0以降はgemとして入れる必要がある。 

## サーバーを起こす  
1. そもそもrubyがあるのか確認`$ ruby -v`  
2. gemがなければ`$ gem install webrick`  
3. `webrick.rb`ファイルを用意
4. カレントディレクトリを確認して`$ ruby webrick.rb`  
5. `webrick.rb`内で指定した`localhost:[ポート番号]`にアクセスし確認  

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

-20220913, 20220922, 20221001