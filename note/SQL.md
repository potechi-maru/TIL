# SQL

`SELECT`：どのカラム
`FROM`：どのテーブル
`WHERE`：カラムと条件（さまざまな演算子）
`AND`：条件の追加
`OR`：条件の追加
`GROUP BY`：グループ化
`ORDER BY`：カラムと並び替え
`LIMIT`：最大で何件取得するか
`JOIN`
`ON`

***クエリの最後に`;`をつける***
***大文字と小文字は区別されない***

## SELECT
```
SELECT *  

SELECT name, age  
```
### DISTINCT
重複するデータを省く。
```
SELECT DISTINCT(name)  
FROM purchases;
```
nameカラムから名前を重複せずに取り出す。

### 四則演算
```
SELECT name, price * 1.1
FROM purchases;
```
商品名とpriceカラムに1.1をかけた金額が取得できる。  
カラムそのものに対して計算式を書けるところ、
計算後のデータが取得できるところがポイント。  
四則演算はWHEREでももちろん使える。  

### SUM/AVG/COUNT/MAX/MIN
```
SELECT SUM(price)  
FROM purchases
WHERE user_name = "maru";
```
sum
```
SELECT AVG(price)  
FROM purchases
WHERE user_name = "maru";
```
average
```
SELECT COUNT(price)  
FROM purchases
WHERE user_name = "maru";
```
null以外のcount
```
SELECT COUNT(*)  
FROM purchases
WHERE user_name = "maru";
```
これならnullも含む。
```
SELECT MAX(price)  
FROM purchases
WHERE user_name = "maru";
```
max  
minも同じように使用。

## WHERE
カラムと条件を指定する。
演算子使える。
```
WHERE age >= 100  

WHERE age IS NULL  

WHERE name IS NOT NULL  

WHERE name = "maru"  

WHERE name LIKE "%maru%"  

WHERE NOT name LIKE "maru%"  


```
とか。  
LIKEは見た通り。同じようなデータを探す。ワイルドカード使える。  
NOTも見た通り。if文で言うたらunlessみたいな。  
NULLはISとセット。`WHERE price = NULL`とかはだめ。
`IS NULL`ならそのカラムにデータがないレコード、
`IS NOT NULL`ならそのカラムにデータがあるレコード。

### OR/AND
```
SELECT *  
FROM users  
WHERE name LIKE "%maru%" 
AND age >= 100;
```
usersテーブルから、名前のどこかに"maru"が入り、
かつ年齢が100歳以上のレコードを取り出す。
```
SELECT *  
FROM users  
WHERE name IS NULL  
OR age IS NULL;  
```
usersテーブルから、名前がない、
もしくは年齢がないレコードを取り出す。

## ORDER BY
```
ORDER BY name DESC
```
## LIMIT
基本最後に書く。
```
SELECT *  
FROM users  
WHERE name LIKE "%maru" 
LIMIT 5;
```
5件取得する。

## GROUP BY
そのカラムで同一のデータを持つレコードをグループ化。  
nullもひとつのグループとして扱われる。  
```
SELECT user_age, SUM(price)  
FROM purchases  
GROUP BY user_age;
```
同じ年齢のレコード達がそれぞれグループ化され、
グループごとの会計の合計値を取得。


---  
忘れているので復習  

-20230210