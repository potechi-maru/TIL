# bootstrapが効かない/プルダウンしない
また君か  
過去の戦いの記録を見つつQiitaも参考にした。  
## とりあえずyarn add

```
$ yarn add jquery bootstrap
```  
```  
warning ../../../package.json: No license field  
[1/4] Resolving packages...  
[2/4] Fetching packages...  
[3/4] Linking dependencies...  
warning " > bootstrap@5.2.3" has unmet peer dependency "@popperjs/core@^2.11.6".  
[4/4] Building fresh packages...  
success Saved lockfile.  
success Saved 2 new dependencies.  
info Direct dependencies  
├─ bootstrap@5.2.3  
└─ jquery@3.6.3  
info All dependencies  
├─ bootstrap@5.2.3  
└─ jquery@3.6.3  
Done in 7.05s.  
```  

以前はwarningが原因なのかと思いwarningとめちゃくちゃ戦っていたが、
warningがエラーの原因ではないとなんとなくわかっているので今回は無視。  
そもそも警告なので無視しても動くというのを以前見かけた。  

## RailsTutorialを参照する

### WebpackにjQueryの設定を追加する
`config/webpack/environment.js`に記載  
```
  const webpack = require('webpack')  
  environment.plugins.prepend('Provide',  
    new webpack.ProvidePlugin({  
      $: 'jquery/src/jquery',  
      jQuery: 'jquery/src/jquery'  
    })  
  )  
```  
### 必要なJavaScriptファイルをrequireまたはimportする
`app/javascript/packs/application.js`に記載  
```
  require("jquery")  
  import "bootstrap"  
```  

上記2つ記載し、サーバー再起動するも効果なし。  
書いた方がよさそうな気がするので消さずにそのままで。困るときが来たら消す。  
以前はbootstrapとjQeryを再インストール後に上記記載して解消したが、
今回は構築が違うので嫌な予感がしてQiitaを探す。  

## popperjs
https://qiita.com/kazutosato/items/c9dfa99d10411ced64b7  
```
$ yarn add bootstrap @popperjs/core jquery  
```  
動いた！！！！！！  
popperjsはbootstrap4以降の依存ライブラリとのこと。  
以前の戦いではbootstrapのバージョンを3系に固定していたため、初めてお目にかかった。  
https://techracho.bpsinc.jp/hachi8833/2021_05_06/83678  

> Bootstrap 5と併用するpopper.jsについてはyarn add @popperjs/coreでインストールするようです。  

今回bootstrapのバージョン指定はしていないため5系を入れている。  
いま見返したら無視したwarningに書いてあるじゃん。

> warning " > bootstrap@5.2.3" has unmet peer dependency "@popperjs/core@^2.11.6".  

---

warningには目を通しましょう。  

--20230121