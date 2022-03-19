---
tags:
  - Nginx
---
#Wordpress Template.
This is the wordpress nginx template. 
You can use this for of course wordpress.
???+ info
  I'm using for this template php7.4 and php7.4-fpm.

``` yaml
server {
    listen 80;
    server_name www.domain.com # (1)! domain.com;
    return 301 https://www.domain.com$request_uri; # (1)!
}

server {
        listen 443;
        listen [::]:433;

    ssl_certificate /etc/letsencrypt/live/www.domain.com # (3)! /fullchain.pem   ;
    ssl_certificate_key /etc/letsencrypt/live/www.domain.com # (4)! /privkey.pem ;

        root /var/www/wordpress;
        index  index.php index.html index.htm;
        server_name www.domain.com # (5)! ;

        error_log /var/log/nginx/mysite.com_error.log;
        access_log /var/log/nginx/mysite.com_access.log;
        
        client_max_body_size 100M;
        location / {
                try_files $uri $uri/ /index.php?$args;
        }
        location ~ \.php$ {
                include snippets/fastcgi-php.conf;
                fastcgi_pass unix:/run/php/php7.4 # (2)!-fpm.sock;
                fastcgi_param   SCRIPT_FILENAME $document_root$fastcgi_script_name;
        }
}
```

1.  Change www.domain.com & domain.com to your domain.
2.  Change php7.4-fpm.sock to your php version. If your using 8.1. Change 7.4 to 8.1.
3.  Change www.domain.com & domain.com to your domain.
4.  Change www.domain.com & domain.com to your domain.
5.  Change www.domain.com & domain.com to your domain.
