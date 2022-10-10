# puts p print return比較

## puts
オブジェクトの出力と改行を交互に行う。  
変数の内容やメソッドの戻り値を出力。  
配列の場合は要素ひとつを出力するごとに改行する。  
putsメソッド自身の戻り値はnil。つまりputsで出力された内容はnil。  
表面だけであり、中身はないといった印象か。  
呼び出すメソッド：`to_s`  

```
puts "15"
  # 文字列
puts 15
  # 数値
```
```
15
15
  # これらはnil
```
```
a = [1, 2, 3]
puts a
```
```
1
2
3
  # これらはnil
```
## p  
オブジェクトの出力と改行を交互に行う。  
文字列のダブルクオートや改行の\\nなども出力する。  
文字列として出力されてしまうため改行は使えない。  
配列は配列として出力される。  
pメソッドの戻り値は渡されたオブジェクトそのものになる。  
putsの戻り値はnilなのに対し、pはnilではなくオブジェクトそのもの。  
呼び出すメソッド：`inspect`  
```
p "15"
  # 文字列
p 15
  # 数値
```
```
"15"
15
  # nilではない
```
```
a = [1, 2, 3]
p a
```
```
[1, 2, 3]
  # nilではない
```
## print  
オブジェクト出力後に改行しない。  
\\nは使えるので改行させることは可能。  
戻り値はnil。  
呼び出すメソッド：`to_s`  
```
print "15"
print "28"
  # 文字列
print "15"
print "28"
  # 数値
```
```
15281528
  # これらはnil
```
```
a = [1, 2, 3]
print a
```
```
[1, 2, 3]
  # これはnil
```
## return
returnの後に書いた値をオブジェクトの戻り値とし、メソッドを終了させる。
```
def fifteen
  return "15"
    # 文字列
  puts "return!"
end
```
上記の場合、戻り値は文字列の"15"である。
戻り値が決まり、メソッドを終了してしまうので`return!`が表示されることはない。
returnは表示させるメソッドではないので何も表示されない。
表示させたい場合はreturnで戻り値を取得した上で、
同メソッド/アクション外でputsなどの表示系メソッドを使う必要がある。
```
def nico
  return "niconico!"
end

puts nico
p nico
```
```
niconico!
  # putsなのでnil
niconico!
  # pなのでnilではない
```
## 省略のreturn
省略できるが、その場合メソッドの終了が発生しない。
最後までそのメソッドを実行する。  
if文など処理を分岐させる場合は注意が必要。
省略のreturnを複数同時に使用する場合は最後の省略returnの内容を戻り値とする。  
最後ではない省略のreturnは戻り値にならない。
```
def nico
  "niconico!"
  "wahaha"
end

puts nico
```
```
wahaha
```

https://www.task-notes.com/entry/20141109/1415520719
https://zenn.dev/nagan/articles/ae479d26e6d2b0
https://qiita.com/keisuke713/items/3bd171559b9d8a7bc500#:~:text=puts%E3%81%AF%E5%87%BA%E5%8A%9B%E3%81%99%E3%82%8B%E6%99%82%E3%81%AB%E3%80%81return%E3%81%AF%E6%88%BB%E3%82%8A%E5%80%A4%E3%82%92%E5%8F%97%E3%81%91%E5%8F%96%E3%82%8B%E6%99%82%E3%82%84%E3%83%A1%E3%82%BD%E3%83%83%E3%83%89%E3%81%8B%E3%82%89%E8%84%B1%E5%87%BA%E3%81%97%E3%81%9F%E3%81%84%E6%99%82%E3%81%AB%E4%BD%BF%E3%81%84%E3%81%BE%E3%81%99%EF%BC%88%E7%9C%81%E7%95%A5%E5%8C%96%E3%81%97%E3%81%9F%E3%82%89%E8%84%B1%E5%87%BA%E3%81%AF%E4%B8%8D%E5%8F%AF%EF%BC%89%E3%80%82%20Register%20as%20a%20new%20user%20and%20use,more%20conveniently%20You%20can%20follow%20users%20and%20tags

-20221009