FROM php:8.1.14-fpm

# COPY php.ini
COPY ./docker/php/php.ini /usr/local/etc/php/php.ini

# Composer install
COPY --from=composer:2.5.1 /usr/bin/composer /usr/bin/composer

# install Node.js
COPY --from=node:18.13.0 /usr/local/bin /usr/local/bin
COPY --from=node:18.13.0 /usr/local/lib /usr/local/lib

RUN apt-get update && \
    apt-get install -y wget git unzip libpq-dev libfreetype6-dev libjpeg62-turbo-dev libpng-dev \
    git \
    zip \
    unzip \
    vim \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install pdo_mysql bcmath

WORKDIR /var/www/html
