# Nginx Templates i use.


[Wordpress Config](/wordpress.conf)
[NameLessMC Config](/namelessmc.conf)


In all of these config files i use CertBot for the HTTPS.

**How to install CertBot with Nginx.**

```
sudo apt update
sudo apt install -y certbot
sudo apt install -y python3-certbot-nginx
```
**How to make a cert.**
```
certbot certonly --nginx -d domain.com
```
