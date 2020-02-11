FROM php:7.3-fpm-alpine

###########################################################################
# https://github.com/mlocati/docker-php-extension-installer
# Install php extensions with their apk dependencies
###########################################################################

ADD https://raw.githubusercontent.com/mlocati/docker-php-extension-installer/master/install-php-extensions /usr/local/bin/
RUN chmod uga+x /usr/local/bin/install-php-extensions && sync && \
    install-php-extensions gd intl xdebug \
    mysqli soap zip calendar xsl gettext \
    bcmath sockets sysvmsg sysvsem sysvshm \
    wddx opcache

###########################################################################
# configure php-fpm
###########################################################################

COPY fpm-pool.conf /usr/local/etc/php-fpm.d/www.conf
COPY php.ini /usr/local/etc/php/conf.d
COPY opcache.ini /usr/local/etc/php/conf.d/opcache.ini
