1~10章末問題やる

x = false
unless x # 条件を満たさない時(条件がnilかfalseとき)に実行する
  puts "アイスかおー"
end
if !x # xの中身を反対にするtrue/false ifなのでtrueなら実行
  puts "アイスかおー"
end

while条件を満たすまで繰り返す

配列
array.pop で末尾削除
array.shift で先頭削除
array.push(object) で末尾追加
array.unshift(object) で先頭追加

each文の処理を途中で終わらせるbreak
array = [1,2,3,4,5]
array.each do |i|
  break if i == 3
  puts i
end
breakの後の条件を満たす場合このeach文のブロック自体を終了する。
>>1
2

each文の処理を途中にして先に進めるnext
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