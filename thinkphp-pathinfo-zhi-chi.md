```
2.thinkphp 隐藏index.php
thinkphp config配置：
'URL_MODEL'          => '2', //URL模式
nginx rewrite配置：
location / { 
   if (!-e $request_filename) {
   rewrite  ^(.*)$  /index.php?s=$1  last;
   break;
    }}
如果你的ThinkPHP安装在二级目录，Nginx的伪静态方法设置如下，其中youdomain是所在的目录名称
location /youdomain/ {
        if (!-e $request_filename){
            rewrite  ^/youdomain/(.*)$  /youdomain/index.php?s=$1  last;
        }
    }
```



