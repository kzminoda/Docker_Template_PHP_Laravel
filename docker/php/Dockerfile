FROM php:8-apache

COPY ./php.ini /usr/local/etc/php
#COPY ./apache2.conf /etc/apache2/conf-enabled
#COPY ./apache2.conf /etc/apache2/conf-available
COPY ./apache2.conf /etc/apache2
#COPY ./mpm_prefork.conf /etc/apache2/mods-enabled
#COPY ./mpm_prefork.load /etc/apache2/mods-enabled
COPY --from=composer /usr/bin/composer /usr/bin/composer

RUN apt-get update
RUN apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng-dev libmcrypt-dev vim libzip-dev zlib1g-dev
#RUN apt-get install -y apache2 apache2-utils apache2-dev libapache2-mpm-itk
RUN docker-php-ext-install mysqli pdo_mysql gd zip
RUN apt-get clean
RUN rm -rf /var/lib/apt/lists/*
#RUN chmod -R 777 /var/www/html

# RUN chown -R www-data:www-data /var/www/html/storage/logs
RUN chmod -R 777 /var/www/

RUN a2enmod rewrite
#RUN a2enmod mpm_prefork
#RUN a2enconf apache2


