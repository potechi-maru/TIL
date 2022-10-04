# TimeZoneの指定  
https://qiita.com/jnchito/items/cae89ee43c30f5d6fa2c
指定しない場合はシステムのタイムゾーンが適用なんだとか。

```
ENV["TZ"] = 'Asia/Tokyo'
```

## WEBrickサーバーの演習にて  
AWSのヘッダーでは東京になっているがサーバーを起こしてアクセスすると
UTCになっていた。  
本来は別のファイルに記述したほうが良いようだが、
試しに`webrick.rb`に記載してみたら期待した通り動いた。  

### UTC  
協定世界時　Coordinated Universal Time  
世界の標準時間のこと

