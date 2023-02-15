# Scope

クラスメソッドのようなもの。
Modelを呼ぶときにどこからでも使えるメソッド。
同じようなSQLを書く場合に定型文的に設定しておくイメージ。
クエリメソッドが連結していると見辛いので、
可読性を上げることができる。
scopeは細かく分けておき、
分けたscopeを使って組み合わせたscopeを定義することができる。
シンプルに書いておいた方が応用も効くし、
予期せぬ処理を避けられる。


> 条件文を評価した結果がfalseになった場合であっても、
スコープは常にActiveRecord::Relationオブジェクトを返します。
クラスメソッドの場合はnilを返すので、この点において振る舞いが異なります。
したがって、条件文を使うクラスメソッドをチェインし、
かつ、条件文のいずれかがfalseを返す場合、
NoMethodErrorを発生する可能性があります。

https://railsguides.jp/active_record_querying.html#%E3%82%B9%E3%82%B3%E3%83%BC%E3%83%97
https://qiita.com/ngron/items/14a39ce62c9d30bf3ac3
https://qiita.com/ozin/items/24d1b220a002004a6351

-230209

