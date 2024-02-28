FROM php:7.4-fpm

RUN docker-php-ext-install pdo_mysql

COPY ./site /var/www/html

COPY php-fpm-pool.conf /etc/php/7.4/fpm/pool.d/www.conf

RUN chown -R www-data:www-data /var/www/html

EXPOSE 9000

CMD ["php-fpm", "-F"]
