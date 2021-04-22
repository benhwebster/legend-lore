# Simple API gateway configs for nginx

Modified from https://www.nginx.com/blog/deploying-nginx-plus-as-an-api-gateway-part-1/ 

place everything in `/etc/nginx`

# Setup SSL with letsencrypt and nginx

modified from https://www.nginx.com/blog/using-free-ssltls-certificates-from-lets-encrypt-with-nginx/

certbot can automatically configure NGINX for SSL/TLS. It looks for and modifies the server block in your NGINX configuration that contains a server_name directive with the domain name you’re requesting a certificate for.

setup certbot:
`$ apt-get update`
`$ sudo apt-get install certbot`
`$ apt-get install python-certbot-nginx`

check and reload configs
`$ nginx -t && nginx -s reload`

get certs:
`$ sudo certbot --nginx -d example.com -d www.example.com`

add crontab job for certbot to renew certs

`$ crontab -e`
`0 12 * * * /usr/bin/certbot renew --quiet`