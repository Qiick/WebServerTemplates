---
title: Letsencrypt
---
# How to get letsencrypt cert.

=== "Letsencrypt Nginx"

    ``` conf
    sudo apt update
    sudo apt install -y certbot
    sudo apt install -y python3-certbot-nginx
    ```
    Make the Cert
    ````
    certbot certonly --nginx -d domain.com
    ````

=== "Letsencrypt Apache"

    ``` conf
    #include <iostream>

    int main(void) {
      std::cout << "Hello world!" << std::endl;
      return 0;
    }
    ```
=== "Letsencrypt Standalone"

    ``` conf
    #include <iostream>

    int main(void) {
      std::cout << "Hello world!" << std::endl;
      return 0;
    }
    ```   
