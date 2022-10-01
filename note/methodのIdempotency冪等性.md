# メソッド  
https://qiita.com/suin/items/d17bdfc8dba086d36115  
### Idempotent  
冪等/巾等/べき等（べきとう）/ Fr idempotent  
1回行っても複数回行っても結果が同じこと。  
成功したリクエストの結果（リソース状態）は実行された回数と無関係であること。  
レスポンスは関係ない。
https://developer.mozilla.org/ja/docs/Glossary/Idempotent  
https://www.infoq.com/jp/news/2014/05/idempotent/  
### POST  
リソースの新規作成  
### PATCH  
既存リソースの一部更新  
### DELETE  
削除。これは冪等である。  
何度リクエストしても”削除された”というリソース状態は変わらない。  
ただしレスポンスは変化する。一度目は200、二度目以降は404。  

-20220921