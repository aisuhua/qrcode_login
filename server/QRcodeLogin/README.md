安装 mongodb 扩展

```sh
pecl install mongodb
```

安装 mongodb client

```sh
composer require mongodb/mongodb=^1.3.2
```

添加 Nginx 站点配置

```nginx
server {
    listen 80;
    server_name qrcode.demo.com;
 
    root /www/web/qrcode_login/server/QRcodeLogin/webroot;
    index index.html index.htm index.php;
 
    location / {
        try_files $uri $uri/ /index.php;
    }
 
    location ~ \.php$ {
        try_files $uri =404;
 
        include fastcgi.conf;
        fastcgi_pass 127.0.0.1:9000;
    }
}
```

访问站点：http://qrcode.demo.com

模拟用户在客户端点击确认登录

http://qrcode.demo.com/client_login.php?user=aisuhua&source=d2313b0591d649da1b5f50341d69265e
