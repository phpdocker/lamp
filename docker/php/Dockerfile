FROM php:7.2-fpm

MAINTAINER me@hranicka.cz

RUN apt-get update && apt-get upgrade -y

RUN apt-get update \
  && apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng-dev \
  && docker-php-ext-install -j$(nproc) pdo pdo_mysql zip mbstring gd iconv

RUN pecl install xdebug-2.6.0

COPY ./php.ini /usr/local/etc/php/
