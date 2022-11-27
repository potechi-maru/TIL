# 自分でバリデーションを作る
## メソッドの定義
モデルの中(もしくは参照先)にメソッドを定義する。  
```  
def method_name
  errors.add ...
end
```  
errorsに自分で書いたエラーの定義を格納するという書き方。  
## バリデーションの定義
```  
validate :method_name  
```  
バリデーションを定義する。
validatesではなく、複数形ではない**validate**  

--221121