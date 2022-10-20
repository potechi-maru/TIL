# unless

```  
x = false  

unless x  
  puts "アイスかおー"  
end  

if !x  
  puts "アイスかおー"  
end  
```  
unless文は条件を満たさない時(条件がnilかfalseとき)に実行する  
if文は条件がtrueなら実行する  

xの値が同じならば`unless`と`if !(条件)`は同じ処理になるはず  

-20221017