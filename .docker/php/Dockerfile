FROM php:7.1-apache

RUN apt-get update && apt-get upgrade -y

RUN apt-get update \
  && apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng12-dev libmcrypt-dev \
  && docker-php-ext-install pdo_mysql mysqli mbstring gd iconv mcrypt

RUN pecl install xdebug-2.5.0 \
    && docker-php-ext-enable xdebug

COPY php.ini /usr/local/etc/php/
