FROM php:8.3-fpm-alpine

# Install necessary dependencies
RUN set -eux \
  && apk add --no-cache \
  bash curl git unzip \
  libpng-dev libjpeg-turbo-dev freetype-dev \
  libxml2-dev libzip-dev oniguruma-dev \
  icu-libs icu-dev \
  mariadb-client

# Install PHP extensions
RUN docker-php-ext-configure gd --with-freetype --with-jpeg \
  && docker-php-ext-install \
  pdo_mysql \
  bcmath \
  mbstring \
  intl \
  opcache \
  zip \
  gd \
  soap \
  xml

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install npm
RUN apk add --no-cache nodejs npm

WORKDIR /var/www/html

EXPOSE 9000

CMD ["php-fpm"]