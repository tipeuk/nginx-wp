# WordPress Docker Container

Lightweight WordPress container with Nginx 1.18 & PHP-FPM 7.3 based on Alpine Linux.

_WordPress version currently installed:_ **5.6**

- Small Docker image size (59MB)
- Built on the lightweight Alpine Linux distribution
- Uses PHP 7.3 for better performance, lower cpu usage & memory footprint
- Optimized to only use resources when there's traffic (by using PHP-FPM's ondemand PM)
- Optimized for 100 concurrent users
- Can safely be updated without losing data
- Fully configurable because wp-config.php uses the environment variables you can pass as an argument to the container

## Usage

See [docker-compose.yml](https://github.com/tipeuk/nginx-wp/blob/master/docker-compose.yml) how to use it in your own environment.

    docker-compose up

Or

    docker run -d -p 80:80 -v /local/folder:/var/www/wp-content \
    -e "DB_HOST=db" \
    -e "DB_NAME=wordpress" \
    -e "DB_USER=wp" \
    -e "DB_PASSWORD=secret" \
    -e "FS_METHOD=direct" \
    tipeuk/nginx-wp

### WP-CLI

This image includes [wp-cli](https://wp-cli.org/) which can be used like this:

    docker exec <your container name> /usr/local/bin/wp --path=/usr/src/wordpress <your command>

## Inspired by

- https://hub.docker.com/_/wordpress/
- https://codeable.io/wordpress-developers-intro-to-docker-part-two/
- https://github.com/etopian/alpine-php-wordpress
