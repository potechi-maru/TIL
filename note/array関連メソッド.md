# 配列
`array.pop` で末尾削除  
`array.shift` で先頭削除  
`array.push(object)` で末尾追加  
`array.unshift(object)` で先頭追加  

# break
each文の処理を途中で終わらせる  
```  
array = [1,2,3,4,5]  
array.each do |i|  
  break if i == 3  
  puts i  
end  
breakの後の条件を満たす場合  
このeach文のブロック自体を終了する  
>>1  
2  
```  

# next  
each文の処理を途中にして先に進める  
```
array = [1,2,3,4,5]
array.each do |i|
  next if i == 3
  puts i
end
nextの後の条件を満たす場合  
そのオブジェクトの処理をそこで終わらせて  
次のオブジェクトの処理に移る  
>>1
2
4
5
```  

# uniqメソッド  
配列から重複した要素を取り除いた新しい配列を作る  
```  
array1 = [1, 3, 7, 5, 5, 1]  
array2 = array1.uniq  
p array1 #=> [1, 3, 7, 5, 5, 1]  
p array2 #=> [1, 3, 5, 7]  
```  
重複しない新しい配列を作るので元の配列が書き換わるわけではない。  

書き換えたい場合はuniq!を使用  
削除した場合はself そうでなければnilを返す
```  
array1 = [1, 3, 7, 5, 5, 1]  
array2 = array1.uniq!  
p array1 #=> [1, 3, 5, 7]  
p array2 #=> [1, 3, 5, 7]  
```  
自身を書き換えるので破壊的変更  
オブジェクトidというオブジェクトごとの識別idを用いて破壊的かどうか検証できる。  
```
p array1.object_id #=> (同じオブジェクトid)  
p array2.object_id #=> (同じオブジェクトid)  
```  

-20221017, 20221019

# sort  
昇順に並び替えるメソッド  
数値なら小さい順、文字列ならアルファベット順  
大文字と小文字がある場合 大文字が先になる aよりZの方が先になる  
降順にしたい場合はreverseメソッドを併用  
```  
array = [3, 5, 1, 7]
array.sort #=> [1, 3, 5, 7]
array.sort.reverse #=> [7, 5, 3, 1]

array2 = [haha, Umm, Ah, oh, Huh]   
array2.sort #=> [Ah, Huh, Umm, haha, oh]  
array2.sort.reverse #=> [oh, haha, Umm, Huh, Ah]  
```   
reverseはソートではなく文字列を逆順にもできる  
```  
"reverse".reverse #=> "esrever"  
```  

--

# map  
配列の要素ひとつずつに処理をして新しい配列を作る  
```  
result = [1, 2, 3].map do |x|  
  x * 2  
end  
p result  

>>
[2, 4, 6]
```  
```  
result = [100, 200, 300].map do |x|  
  "#{x}円"  
end  
p result  

>>  
["100円", "200円", "300円"]  
```  

--20221020