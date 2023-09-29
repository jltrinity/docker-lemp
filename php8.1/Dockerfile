FROM php:8.1-fpm

# Install any PHP extensions you need here
# For example:
RUN docker-php-ext-install pdo pdo_mysql

WORKDIR /var/www/html

# Copy your application code into the container
#COPY . .

EXPOSE 9000

CMD ["php-fpm"]