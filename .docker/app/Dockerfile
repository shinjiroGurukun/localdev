FROM php:8.0-apache

COPY --from=composer /usr/bin/composer /usr/bin/composer

RUN apt-get update \
  && apt-get install -y wget git unzip libzip-dev zlib1g-dev libfreetype6-dev libjpeg62-turbo-dev libpng-dev \
  && docker-php-ext-configure gd --with-freetype --with-jpeg \
  && docker-php-ext-install zip pdo_mysql gd \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* \
  && a2enmod rewrite

RUN apt-get update \
  && apt-get install -y nodejs npm\
  && npm install n -g \
  && n stable \
  && apt-get purge -y nodejs npm

RUN npm install --global yarn