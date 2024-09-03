FROM php:8.2-fpm

# 必要なPHP拡張モジュールをインストール
RUN apt-get update && apt-get install -y \
    zip \
    unzip \
    && docker-php-ext-install pdo pdo_mysql

# Composerをインストール
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# php.iniをコピー
COPY php.ini /usr/local/etc/php/

# 作業ディレクトリを設定
WORKDIR /var/www/html

# Laravelをインストール
RUN composer create-project --prefer-dist laravel/laravel .

# パーミッションを設定
RUN chown -R www-data:www-data /var/www/html/storage /var/www/html/bootstrap/cache

