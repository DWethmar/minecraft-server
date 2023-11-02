# minecraft-server
minecraft server config files

some setup:
-  openssl req -newkey rsa:2048 -nodes -keyout nginx/domain.key -out nginx/domain.csr

Obtain the SSL Certificate
 - docker-compose run --rm certbot certonly --webroot --webroot-path=/var/www/certbot -d your_domain.com
 - docker-compose restart nginx

Automate Renewal
- 0 0,12 * * * /usr/bin/docker-compose -f /path/to/your/docker-compose.yml run --rm certbot renew --webroot --webroot-path=/var/www/certbot && /usr/bin/docker-compose -f /path/to/your/docker-compose.yml exec nginx nginx -s reload
