# checkoutコマンドについて  

## ブランチの切り替え  
### 単純なブランチの切り替え  
```
$ git checkout <branchname>
$ git switch <branchname>
```  
switchコマンドは追加実装されたもの。  
どちらでも同じ動き。  

### ひとつ前にいたブランチに切り替え
```
$ git checkout -
```

### ブランチの新規作成＋切り替え
```
$ git checkout -b <newbranchname>
$ git switch -c <newbranchname>
```

### ブランチの上書き作成＋切り替え  
```
$ git checkout -B <newbranchname>
$ git switch -C <newbranchname>
```
既に同名のブランチがあった場合でも
存在したブランチを削除して作成する。  
作成後は作成したブランチに切り替え。
オプションを大文字にするだけなので誤らないよう注意。  

## 内容を変化させる  
```
$ git init
  # 初期化
```
```
$ git add/rm/mv
  # 作業ディレクトリ **->** ステージングエリア

$ git checkout -- <filename>
  # 作業ディレクトリ **<-** ステージングエリア
```
```
$ git commit
  # ステージングエリア **->** Gitディレクトリ

$ git reset HEAD <filename>
  # ステージングエリア **<-** Gitディレクトリ
```

### 作業ディレクトリをステージングエリアの状態に戻す
```
$ gti checkout -- <filename>
```
指定したファイルを作業ディレクトリの状態から
ステージングエリアの状態に戻す。
ステージングしているがcommitしていない場合に使える。  
ステージングした後にファイルを編集(削除含む)したが
その変更をなかったことにしたい場合など。  

### ステージングエリアを最新のcommitの状態に戻す
```
$ git reset HEAD <filename>
```
指定したファイルをステージングされた内容から
最新のcommitの内容に変更する。  
ステージングしている場合に使える。
ステージング状態はそのままに、
既にcommitした内容に差し替える。
つまり、ワークツリーで行った変更は
ステージングされていない状態になる。  
ステージングしたがその変更をなかったことにしたい場合など。



https://qiita.com/yunano/items/f3133ea64efed762df2f  
https://www.slideshare.net/matsukaz/git-28304397  

-20221014