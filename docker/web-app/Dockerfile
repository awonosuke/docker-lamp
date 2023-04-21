FROM php:7.4-apache

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

RUN apt-get update && apt-get install -y --no-install-recommends \
  libicu-dev \
  zip \
  unzip \
  git \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* \
  && docker-php-ext-install \
  intl \
  pdo_mysql
#  && a2enmod rewrite # if you need to enable mod_rewrite remove the # from the beginning of this line

COPY ./docker/web-app/php.ini ${PHP_INI_DIR}

WORKDIR /var/www/html