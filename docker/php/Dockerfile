FROM php:8.1-fpm

RUN apt-get update \
 && apt-get install -y \
    git \
    zip \
    unzip \
    vim \
    libpq-dev \
 && docker-php-ext-install \
    pdo_mysql \
    mysqli

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/public
