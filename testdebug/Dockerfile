FROM php:7.4-apache

ENV XDEBUG_PORT 9003
ENV XDEBUG_IDEKEY docker

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y git
 
RUN git clone --depth 1 "https://github.com/xdebug/xdebug" \
 && cd xdebug \
 && phpize \
 && ./configure \
 && make \
 && make install \
 && docker-php-ext-enable xdebug
 
RUN echo "xdebug.mode=debug" >> /usr/local/etc/php/conf.d/xdebug.ini && \
    echo "xdebug.start_with_request=yes" >> /usr/local/etc/php/conf.d/xdebug.ini && \
    echo "xdebug.trace_format=1" >> /usr/local/etc/php/conf.d/xdebug.ini && \
    echo "xdebug.client_port=${XDEBUG_PORT}" >> /usr/local/etc/php/conf.d/xdebug.ini && \
    echo "xdebug.idekey=${XDEBUG_IDEKEY}" >> /usr/local/etc/php/conf.d/xdebug.ini