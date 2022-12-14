# NotFound  
Cloud9でwebrickサーバーを起こして、localhostにアクセスすると
Notfoundになる問題が発生。  

# 原因  
サーバーを起動した場所に対し、見るべきURLが間違っている。  

# 詳しく  
そもそもCloud9で`localhost`というアドレスにアクセスすることは多分ない。  
”NotFoundが返される”というサーバーとして起動している状態になっていたのは
ローカルでターミナルから起動コマンドを打ってそのまま放置していたから。  
見れていた日もあったのに
`'/'NotFound`と表示されルートすら見れなくなっていたのは、
ローカルにあった`webrick.rb`を削除していたから。  
見れていた日はすべてローカルで実行していたようだ。  
ローカルで起こしたサーバーのエラーに対し、
クラウドで起こしているサーバーだと思い込み
必死にクラウドでファイル変更していたということ。

# 解決策  
1. ポート番号をAWSがサポートしているものに変更する
2. サーバーを起こしたときにターミナルにポップアップするURLにアクセスする

# 学んだこと  
* Cloud9はクラウドなのでアクセスするアドレスはlocalhostではない。
(ただしIPとして使う場面もあるよう。
https://docs.aws.amazon.com/ja_jp/cloud9/latest/user-guide/app-preview.html)
* 使っていないターミナルはウィンドウを閉じる。
* 起こしたサーバーは終了させる。

-20221002, 20221003, 20221004