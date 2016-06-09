FROM php:5.6-apache

ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_RUN_DIR /var/run/apache2

# allow sites
COPY 000-default.conf /etc/apache2/sites-available/
COPY default-ssl.conf /etc/apache2/sites-available/
COPY ssl-cert-snakeoil.pem /etc/ssl/certs/ssl-cert-snakeoil.pem
COPY ssl-cert-snakeoil.key /etc/ssl/private/ssl-cert-snakeoil.key

RUN a2ensite 000-default
RUN a2ensite default-ssl

# allow modules
RUN a2enmod rewrite
RUN a2enmod ssl

COPY php.ini /usr/local/etc/php/

EXPOSE 443

RUN apt-get update \
  && apt-get install -y vim less libfreetype6-dev libjpeg62-turbo-dev libpng12-dev libmcrypt-dev \
  && docker-php-ext-install pdo_mysql mysqli mbstring gd iconv mcrypt
