# HEADとは  
自分が作業しているブランチの最新のコミットのこと。  
そうでない場合もある(detached HEAD状態)
ブランチを指すもの(ポインタ)

## 
```
$ git reset HEAD <filename>
```
指定したファイルをステージングされた内容から
最新のcommitの内容に変更する。  
ステージング状態はそのままに、
既にcommitした内容に差し替える。
ワークツリーでの変更はステージングされていない状態になる。

https://qiita.com/ymzkjpx/items/00ff664da60c37458aaa  

https://learngitbranching.js.org/?locale=ja  
まずはここから、次のレベルに進もう をやった

-20221014, 20221015