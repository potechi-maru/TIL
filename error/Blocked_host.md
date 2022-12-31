# Blocked host

`$ rails server`サーバー起動後に`Blocked host ホスト名`というエラ―が出たら  
`config/environments/development.rb`に次の文を記載。  
```
config.hosts.clear
```

エラーで勧められるのは次の記載。  
```
config.hosts << "なんちゃらかんちゃら.com"
```

https://qiita.com/kodai_0122/items/67c6d390f18698950440  
今回はRails Tutorialに沿って直したが、後者の方がセキュリティ上良さそう。  
ホワイトリストをクリアにするか、ホワイトリストに追加するかという違い。  

-20221215