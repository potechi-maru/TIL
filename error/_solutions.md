# 初心者向け エラー解決の基本

https://m.youtube.com/watch?v=5fyrGslhUcY  

## 最低限
* エラーログ読む
* デバッガ―を使う  

## 開発環境なら
ブラウザエラー画面の`full trace`を押すと、
どのようなコードを辿ってきたのかわかる。  
ハイライトされているコードに問題がなさそうな時に活用。  

## 次のステップ
* gemのりどみとかgithubのwikiとか読む
* 質問しようとしてみる(テディベア効果 理路整然と説明しようすると自分でおかしさに気づくことがある)
* エラーを再現するのが大変な場合(メールの送信とか)はテストを書いて再現する
* 大きなアプリなら、エラーを再現するためだけの単純なアプリを作り同じエラーが起きたらそちらでデバッグする  

## 注意すること
* やみくもに試さずに、あたりをつけ仮説と検証を繰り返す
* 時間を区切る。諦めて聞いた方が早いし時間を無駄にしない
* ネットのコピペは注意(公式じゃないコードは別の問題を引き起こす可能性あり)
* stackoverflowはBAよりも投票数を気にする(投票数多い方がみんなの役に立っている)  

## おすすめのgem
* better errors
* binding of caller  

### 感想  
なんじゃそりゃ～！！な情報はなく、
視聴を通して知っていることを再確認した。  
やはりログからは逃げられない。  
full traceは知らなかったので次に遭遇した際は試したい。  
おすすめgemも知らなかったのでアプリ開発の際取り入れようと思う。  

-20221015