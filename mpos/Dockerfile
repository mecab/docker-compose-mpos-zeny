FROM webdevops/php-nginx:debian-8
#FROM php:7.1-fpm-jessie

MAINTAINER mecab <mecab@misosi.ru>

WORKDIR /app

#RUN apt-get update && \
#    apt-get -y install git memcached mysql-client zlib1g-dev libmemcached-dev

RUN apt-get update && \
    apt-get -y install git memcached mysql-client php5-memcached php5-mysqlnd php5-curl php5-json

RUN git clone git://github.com/MPOS/php-mpos.git . && \
    git checkout master;
# RUN pecl install memcached

# RUN apt-get -y install libcurl4-gnutls-dev

# RUN docker-php-ext-enable memcached
# RUN docker-php-ext-install mysqli curl json

COPY ./opt/docker/provision/entrypoint.d/8-memcached.sh /opt/docker/provision/entrypoint.d/8-memcached.sh
RUN chmod +x /opt/docker/provision/entrypoint.d/8-memcached.sh
COPY ./opt/docker/etc/nginx/vhost.conf /opt/docker/etc/nginx/vhost.conf
COPY ./opt/docker/etc/nginx/conf.d/01-realip.conf /opt/docker/etc/nginx/conf.d/01-realip.conf
COPY ./mpos/include/classes/coins/coin_yescrypt.class.php /app/include/classes/coins/coin_yescrypt.class.php

# RUN chown -R application:application .
RUN chown -R application:application templates/compile templates/cache logs

COPY ./install-schema /bin
RUN chmod +x /bin/install-schema

ENV WEB_DOCUMENT_ROOT /app/public

