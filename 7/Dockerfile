FROM php:7-apache
RUN apt-get update && \
    apt-get install -y \
        zlib1g-dev libwebp-dev libjpeg62-turbo-dev libpng-dev libxpm-dev libfreetype6-dev libmagickwand-dev
RUN pecl install imagick
RUN docker-php-ext-install mysqli pdo_mysql gd
RUN docker-php-ext-enable imagick
RUN a2enmod rewrite