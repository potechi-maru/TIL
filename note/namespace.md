## 名前空間  
別々のクラスに同じクラス名を使いたい場合に、
モジュール(またはクラス)を使うことで可能になる。  
インスタンスを作らない場合はモジュールが適切。  
作る場合はクラスを使用する。  
`<Class>::<Module>`や`<Module>::<Class>`など、
クラス(モジュール)の間を`::`で繋ぐことで
同じ名前でも使い分けることができる。  
```  
module HelloCafe  
  class Coffee  
    def self.info  
      "まろやかなコーヒー"  
    end  
  end  
end  

module BonjourCafe  
  class Coffee  
    def self.info  
      "渋いコーヒー"  
    end  
  end  
end  

puts HelloCafe::Coffee.info #=> "まろやかなコーヒー"  
puts BonjourCafe::Coffee.info #=> "渋いコーヒー"  

```  

--20221022