FROM php:8.1.0-fpm-alpine
WORKDIR /var/www/html

RUN apk add --update
RUN docker-php-ext-install pdo pdo_mysql

RUN docker-php-ext-install opcache

COPY .docker/php/opcache.ini /usr/local/etc/php/conf.d/opcache.ini
COPY .docker/php/php-fpm.ini /usr/local/etc/php/conf.d/php-fpm.ini

RUN apk add --no-cache \
        freetype-dev \
        libjpeg-turbo-dev \
        libpng-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd

#Install Redis
RUN apk add --no-cache $PHPIZE_DEPS \
    && pecl install redis \
    && docker-php-ext-enable redis

RUN mkdir -p /var/www/html/storage/logs \
    && touch /var/www/html/storage/logs/laravel.log
# Fix rights
RUN chown -R www-data:www-data /var/www/html
RUN chmod -R 775 /var/www/html/storage



# Install Composer
COPY --chown=www-data:www-data . /var/www/html

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
RUN composer self-update

ENV COMPOSER_ALLOW_SUPERUSER=1
RUN set -eux;
#RUN composer install

RUN sed -i 's/9000/9012/' /usr/local/etc/php-fpm.d/zz-docker.conf
