# findとfind_byの使い分け  
findはnilに対してエラーを返す。  
セッション切れになるとエラーになってしまうので
ログイン機構などではfind_byを使用する。  

--20221122