FROM php:5-apache
RUN docker-php-ext-install mysqli
RUN apt-get update &&\
    apt-get install -y \
    libmcrypt-dev
RUN docker-php-ext-install mcrypt
RUN a2enmod rewrite