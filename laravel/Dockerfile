FROM php:7.4-cli

WORKDIR /var/www

RUN apt-get update
RUN apt-get install nano -y
RUN apt-get install libzip-dev -y
RUN docker-php-ext-install zip

RUN php -r "copy('http://getcomposer.org/installer','composer-setup.php');"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"

RUN php composer.phar create-project --prefer-dist laravel/laravel laravel

ENTRYPOINT [ "php", "laravel/artisan", "serve" ]
CMD [ "--host=0.0.0.0" ]