# デジタル署名  

ハッシュ化と公開鍵暗号方式を利用した署名  
公開鍵暗号方式の逆手順を行っている。  

## 目的  
署名する側(=送信者)がなりすましを受けていないことを証明する。  
データを安全に送るための仕組みではない。安全に送る仕組みは後述  

## 手順  
1. 送信者の鍵セットを用意
2. 送るデータをハッシュ化したハッシュ値を用意
3. 2のハッシュ値を**送信者の秘密鍵**で暗号化
4. 元データと、3の'元データのハッシュ値を暗号化したデータ'を送る
5. 受信者は元データをハッシュ化
6. 受信者は3を送信者の公開鍵で複合  
7. 5と6を比較して相違がないことを確認
* ハッシュ化したデータを元に戻すのは不可能なので
秘密鍵で暗号化してもセキュリティ上問題ない。  
* 6の送信者の公開鍵で複合できた時点で
送信者の秘密鍵で暗号化されたことの証明になり
なりすましではないとわかる。  
* 同じデータを同じロジックでハッシュ化すると
同じハッシュ値になるため、
5と6が一致していれば改ざんがないとわかる。

## 具体的に考える  
*送信者：署名する ショメさん*  
*受信者：署名される サレさん*  
ショメさんは南京錠のようなものとその鍵を作りました。  
これらはそれぞれ暗号化する機能を持ち、
またそれを互いに複合化することができる対の存在です。  
南京錠のようなものには`ショメ錠`と名付けました。  
ショメ錠は触れられたとしてもセキュリティ上のリスクはありません。  
対となる鍵がなければ開けることができないからです。  
対となる鍵には`ショメ秘`と名付けました。  
ショメ秘は世界に一つしかない特別な鍵です。  
触れられても開けることはできないショメ錠を
開けることができる唯一の鍵です。  
ショメ秘が奪われてしまうとショメ錠は開いてしまいます。  
それは困るのでショメ秘はショメさんが持っています。  
さて、ショメさんはサレさんから契約書に署名を求められました。  
直接会ったり郵送したりするのは面倒なのでオンラインでやり取りすることにします。  
まずショメさんはもらった契約書に署名します。  
しかしこの署名したデータをただ送るだけでは
ショメさんが署名したという証明になりません。  
サレさんが受け取った段階でなりすましや改ざんを受けている可能性があります。  
そこでショメさんはまず署名済契約書をハッシュ化しました。  
このハッシュ化の手順はサレさんにも共有します。  
続いて、ショメさんだと証明するために、このハッシュ値に鍵をかけることにします。  
オンラインのやり取りでショメさんだと証明できるものといえば、
世界に一つ、ショメさんしかもっていないショメ秘があります。  
ショメさんはハッシュ値にショメ秘を利用して暗号化し鍵をかけます。  
そして、①署名済契約書・②**ショメ秘で鍵をかけた**署名済契約書の**ハッシュ値**・
③ショメ秘を複合化するための**ショメ錠** をサレさんにメールで送ります。  
併せて ④ハッシュ化した手順 もサレさんに教えます。  
さあ、ショメさんのメールを受け取ったサレさんは
ショメさんの署名だと証明できるか試してみます。  
まず、ショメさんに教えてもらった ④ハッシュ化の手順 で
①署名済契約書 をハッシュ化します。  
次に、②ショメ秘で暗号化した署名済契約書のハッシュ値 を
 ③ショメ錠 で複合します。
複合すると、暗号化されていない、
**ショメさん自身がハッシュ化した署名済契約書**が出てきます。  
これで、**サレさんがハッシュ化した署名済契約書**と
**ショメさん自身がハッシュ化した署名済契約書**がそろいました。  
ハッシュ化の手順を同じにすると同じデータは同じハッシュ値になるのです。  
サレさんはハッシュ化の手順をショメさんに教えてもらっているので、
2人の作ったハッシュ値が同じになることで、
改ざんやなりすましが起きていない**ショメさんの署名**であると証明できます。



## 対する公開鍵暗号方式  
1. 受信者の鍵セットを用意
2. 送信者は**受信者の公開鍵**で暗号化
3. 受信者は受信者の秘密鍵で複合化

## 応用：安全に送るデジタル署名  
デジタル署名でデータを送受信する際に、
**受信者の鍵セット**で暗号化・複合化することで
盗聴リスクも防ぐことができる。  
1. 送信者の鍵セットと受信者の鍵セットを用意
2. 送るデータをハッシュ化したハッシュ値を用意
3. 2のハッシュ値を**送信者の秘密鍵**で暗号化
4. 元データと、3の'元データのハッシュ値を暗号化したデータ'を
**受信者の公開鍵**で暗号化して送る
5. 受信者は4を**受信者の秘密鍵**で複合化する
6. 受信者は元データをハッシュ化
7. 受信者は3を送信者の公開鍵で複合 
8. 6と7を比較して相違がないことを確認  

---  

https://wa3.i-3-i.info/word1828.html  

https://www.youtube.com/watch?v=lT7vLRBwxrY&t=923s  

-20221016