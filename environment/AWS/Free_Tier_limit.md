# Free Tier limit alert

> AWS Free Tier usage limit alerting via AWS Budgets	MM/DD/YYYY

> Dear AWS Customer,

> Your AWS account XXXXXXXXXXXX has exceeded 85% of the usage limit for one or more AWS Free Tier-eligible services for the month of X.

> | Product	| AWS Free Tier Usage as of MM/DD/YYYY | Usage Limit | AWS Free Tier Usage Limit |
> | ------- | ------------------------------------ | ----------- | ------------------------- |
> | AmazonEC2 |	26.0080641 GB-Mo | 30 GB-Mo	| 30 GB of Amazon Elastic Block Storage in any combination of General Purpose (SSD) or Magnetic |

> To learn more about your AWS Free Tier usage, please access the AWS Billing & Cost Management Dashboard. You can find more information on AWS Free Tier here.

毎月こんなメールが。
簡単に言えば、「あなた無料枠のうち85%使ってるからそろそろ100%超えるのでお金とりますよ～」というお知らせ。   
なかなか親切。現代っ子らしくメールを見ないので数か月後とかに気が付く。  
来月にならないと何とも言えないが、**多分**解決したのでまとめ。


## 請求の詳細  
https://us-east-1.console.aws.amazon.com/billing
この左のタブから**請求書**を選ぶと当月の詳細が見られる。  
請求書ページをスクロールすると**詳細**という項目があり、
**AWS のサービスの料金**→**Elastic Compute Cloud**→**Asia Pacific (Tokyo)**を開くと請求の詳細が見られる。  

> | $0.12 per GB-month of General Purpose SSD (gp2) provisioned storage - Asia Pacific (Tokyo) | 8.972 GB-Mo | $1.08 |  

という感じで無料枠の30GBを超えた分が請求される。  
全く気が付いてなかったけど7, 9, 10月は請求が発生していた。笑  
アラートメールが来ているだけで実際に無料枠を超えていなくて請求されていないと思っていた。  


## 参考にしたURL 
同じ請求の人　　
https://qiita.com/NoOne/items/1ea743baf6305a4ccbdf  

同じ悩みの人
https://teratail.com/questions/300171  

請求の仕組み  
https://aws.amazon.com/jp/premiumsupport/knowledge-center/ebs-volume-charges/  

EC2の説明  
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-describing-volumes.html  



## 原因  
EBSボリュームが複数存在すること（多分）  

## 個人的な原因  
**深く考えずにインスタンスを作っていたこと。**  
チュートリアル用、ポートフォリオ用、TIL用と分けていた。  
3つのインスタンスとそれぞれに紐づくEBSボリュームがあった。  

以前この請求について調べたときはインスタンスの停止だけで終わらせていたが
**インスタンスを停止するだけでは請求される**とのこと。  

## EC2インスタンスを削除(終了)させた
インスタンスIDの横の項目がシャットダウンになり、リロードすると終了済みになる。  
数日経てばインスタンスのリストからも消えるとのこと。  
インスタンスの削除だけでは解決せずボリュームも削除すると効果があったと
Qiitaの記事では書かれているが、仕様変更なのか、
インスタンスを削除して終了状態にすると連動するボリュームが
ボリュームのリストからは消えてしまった。  
先にボリュームを削除しようとしてもグレーアウトになり選択できなかったので
連動するインスタンスを消す必要があるのかもしれない。  
興味がわかないのでAWSの仕組みについては深追いしません。  

## 感想  
初学者ゆえに消したらまずいのかなと思い環境ごと取っておいていたが
冷静に考えればリモートリポジトリがあるし多分大丈夫。  
困ったら困ったときに考えます。  
とりあえずローカルとリモートに差異がないか確認し、
差異があるものはPushしてからインスタンスを消した。  

EC2インスタンスとかEBSボリュームとかなんだかよくわからないけど
考えるのが面倒くさい。理解は未来の自分に任せて、
とりあえず今は請求されなきゃ良し！ということで。  

--20221116, 20221118