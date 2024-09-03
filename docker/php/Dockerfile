FROM php:8.2-fpm
RUN docker-php-ext-install pdo pdo_mysql
COPY php.ini /usr/local/etc/php/
WORKDIR /var/www/html

