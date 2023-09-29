FROM php:8.1-fpm

WORKDIR /var/www/html

RUN apt update && apt-get update \
    && apt install -y zlib1g-dev g++ git libicu-dev zip libzip-dev zip libxslt1-dev\
    && docker-php-ext-install intl \
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip \
    && docker-php-ext-install xsl

RUN docker-php-ext-install mysqli pdo pdo_mysql

EXPOSE 9000

CMD ["php-fpm"]