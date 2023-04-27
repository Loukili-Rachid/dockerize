FROM php:8.1.0-fpm-alpine

WORKDIR /var/www/html


RUN apk add --no-cache --virtual builddeps \
    && apk add --update \
    && docker-php-ext-install pdo pdo_mysql \
    && docker-php-ext-install opcache


RUN docker-php-ext-install opcache

COPY .docker/cronjob/crontab /etc/crontabs/root

RUN touch /var/log/cron.log

CMD ["crond", "-f"]
