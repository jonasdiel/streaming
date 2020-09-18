FROM php:7.2-fpm-alpine
RUN docker-php-ext-install mbstring tokenizer mysqli pdo_mysql
RUN apk add --no-cache ffmpeg
COPY ./php.ini "$PHP_INI_DIR/php.ini"
VOLUME /var/www/html/storage/media/hls
#FIXME Ajsutar permissão
RUN chmod 777 -R /var/www/html/storage/media/hls