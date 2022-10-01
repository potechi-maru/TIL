# WEBrick  
単純なHTTPwebサーバー機能Rubyのライブラリのひとつ。 
Ruby3.0で削除されたため、3.0以降はgemとして入れる必要がある。 

## サーバーを起こす  
1. そもそもrubyがあるのか確認`$ ruby -v`  
2. gemがなければ`$ gem install webrick`  
3. `webrick.rb`ファイルを用意
4. カレントディレクトリを確認して`$ ruby webrick.rb`  
5. `webrick.rb`内で指定した`localhost:[ポート番号]`にアクセスし確認  

-20220913, 20220922