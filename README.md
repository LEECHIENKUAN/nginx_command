
# Nginx 指向設定
注意：rewrite 最後分成兩種不同的代碼，即 permanent 代表「301永久跳轉」，而 redirect 代表「302臨時跳轉」，只需選擇其一使用即可！兩種跳轉在展現方式上無任何區別，但是302更容易被搜尋引擎視爲SPAM，而301則不會有這些問題！

# Nginx 301 永久指向
從網址的路徑取得參數
```
if ($request_uri ~ "/path/(.*)/(.*)") {
    redirect /page.html?param1=$1&param2=$2 permanent;
}
```
判斷主機
```
if ($host != "www.old.com){  
  rewrite ^/(.*)$ http://www.a.com/$1 permanent;
}
```

# Nginx 302 臨時指向

從網址的路徑取得參數
```
if ($request_uri ~ "/path/(.*)/(.*)") {
    redirect /page.html?param1=$1&param2=$2 redirect;
}

判斷主機
```
if ( $host != "www.old.com" ) {  
  rewrite ^/(.*)$ http://www.a.com/$1 redirect;
}
```
