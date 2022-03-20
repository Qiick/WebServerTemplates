---
title: Letsencrypt
---
# How to get letsencrypt cert.

=== "Letsencrypt with Nginx"

    Install Certbot
    ``` conf
    sudo apt update
    sudo apt install -y certbot
    sudo apt install -y python3-certbot-nginx
    ```
    Make the Cert
    ````
    certbot certonly --nginx -d domain.com
    ````

=== "Letsencrypt with Apache"

    Install Certbot
    ``` conf
    sudo apt update
    sudo apt install -y certbot
    sudo apt install -y python3-certbot-apache
    ```
    Make the Cert
    ````
    certbot certonly --apache -d domain.com
    ````
    
=== "Letsencrypt with Standalone"

    Install Certbot
    ``` conf
    sudo apt update
    sudo apt install -y certbot
    ```
    Make the Cert
    ````
    certbot certonly --standalone -d domain.com
    ````  

??? tip

    Make the Cert first and then point it to your files. If you dont. You get an error.
