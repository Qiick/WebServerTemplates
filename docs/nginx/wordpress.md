---
tags:
  - Nginx
---
#Wordpress Template.
This is the wordpress nginx template. 
You can use this for of course wordpress.
???+ info
  I'm using for this template php7.4 and php7.4-fpm.
=== "Wordpress with Letsencrypt"

    ``` Wordpress with Letsencrypt 
    server {
    listen 80;
    server_name www.domain.com domain.com;
    return 301 https://www.domain.com$request_uri; (1)!
    }

    server {
        listen 443;
        listen [::]:433;

    ssl_certificate /etc/letsencrypt/live/www.domain.com/fullchain.pem   ;
    ssl_certificate_key /etc/letsencrypt/live/www.domain.com/privkey.pem ;

        root /var/www/wordpress;
        index  index.php index.html index.htm;
        server_name www.domain.com;

        error_log /var/log/nginx/mysite.com_error.log;
        access_log /var/log/nginx/mysite.com_access.log;
        
        client_max_body_size 100M;
        location / {
                try_files $uri $uri/ /index.php?$args;
        }
        location ~ \.php$ {
                include snippets/fastcgi-php.conf;
                fastcgi_pass unix:/run/php/php7.4-fpm.sock;
                fastcgi_param   SCRIPT_FILENAME $document_root$fastcgi_script_name;
        }
    }
    ```

=== "Wordpress with Cloudflare SSL"

    ``` Wordpress with Cloudflare SSL
    server {
    listen 80;
    server_name www.domain.com domain.com;
    return 301 https://www.domain.com$request_uri; (1)!
    }

    server {
        listen 443;
        listen [::]:433;

    ssl_certificate /etc/ssl/cert.pem ;
    ssl_certificate_key /etc/ssl/key.pem;

        root /var/www/wordpress;
        index  index.php index.html index.htm;
        server_name www.domain.com;

        error_log /var/log/nginx/mysite.com_error.log;
        access_log /var/log/nginx/mysite.com_access.log;
        
        client_max_body_size 100M;
        location / {
                try_files $uri $uri/ /index.php?$args;
        }
        location ~ \.php$ {
                include snippets/fastcgi-php.conf;
                fastcgi_pass unix:/run/php/php7.4-fpm.sock;
                fastcgi_param   SCRIPT_FILENAME $document_root$fastcgi_script_name;
        }
    }
    ```
