# WP-Dockerized

This repository contains a Dockerized version of WordPress. The intended configuration is Nginx,PHP-FPM & MySQL. 
Hence this repository uses the wordpress:6.1.1-fpm-alpine instead of the default wordpress:latest image, which contains apache as well.

## Prerequisites

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

## Getting Started

1. Clone the repository: `git clone https://github.com/javidrazack/wp-dockerized.git`
2. Navigate to the repository directory: `cd wp-dockerized`
3. Create an .env file to provide the environment variables. You can copy the .env-sample & change the values as per your requirement.

```bash
cp .env-sample .env
```
4.Start the containers: 
 ```bash
 docker-compose up -d
 ```
5. You can access the Wordpress site at http://localhost/
6. You will be prompted to complete the installation.

## Configurations

You can change the default port 80 to any other available port by simply changing the *ports* under the *nginx* service in the  docker-compose.yml file.

```
services:
  nginx:
    build:
      context: .
      dockerfile: nginx/Dockerfile
    ports: 
      - "8080:80"
```
The change binds 8080 to port 80 of nginx container.

The .env file contains the credentials for MySQL database & Wordpress. Additional Wordpress configurations such as enabling Debug can be set by adding 
```
WORDPRESS_DEBUG=true
```
The other possible environment variables can be found [here](https://github.com/docker-library/wordpress/blob/master/latest/php8.2/fpm-alpine/wp-config-docker.php)
