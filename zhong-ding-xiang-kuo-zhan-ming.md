nginx配置

```
server {
  index index.html index.php;
  location / {
    if ($request_uri ~ ^/(.*)\.html$) {  return 302 /$1;  }
    try_files $uri $uri/ $uri.html $uri.php?$args;
  }
  location ~ \.php$ {
    if ($request_uri ~ ^/([^?]*)\.php($|\?)) {  return 302 /$1?$args;  }
    try_files $uri =404;
    # add fastcgi_pass line here, depending if you use socket or port
  }
}
```



