# safe navigation operator  
ぼっち演算子はレシーバがnilのときにエラーを出したくない場面で使用する。  
## 比較
```
object.method
```
objectが空(nil)の場合`no method error for NilClass`  
エラーになってしまう。  
```  
object&.method  
```  
objectが空(nil)の場合**戻り値にnilを返すメソッド**になる。  

--221122