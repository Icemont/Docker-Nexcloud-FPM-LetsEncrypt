# Docker Nexcloud PHP-FPM with Let's Encrypt

## Disclamer!
This solution is not recommended as a production version!
This is just an example - how you can quickly get a working Nextcloud instance up and running, for testing and discovering functionality, with Docker and image with PHP-FPM and with SSL from Let's Encrypt.

## Information
Detailed information and description: <a href="https://icemont.dev/docker/docker-nexcloud-fpm-letsencrypt" target="_blank">https://icemont.dev/docker/docker-nexcloud-fpm-letsencrypt </a>

## Quick Start

```bash
git clone https://github.com/Icemont/Docker-Nexcloud-FPM-LetsEncrypt.git
cd Docker-Nexcloud-FPM-LetsEncrypt
```

Edit the .env file, changing the configuration to your own (few parameters):

```dotenv
# root password for MySQL server
MYSQL_ROOT_PASSWORD=topsecret
# Password for the MySQL database user
MYSQL_PASSWORD=secret

# E-mail address for ACME account registration for Let's Encrypt
CERTBOT_EMAIL=mail@example.com
# Domain for SSL certificate from Let's Encrypt (Your domain or subdomain, for which you have set up A record in DNS
DOMAIN_NAME=example.com
```

Then start building and running the test environment:

```bash
docker-compose up -d
```