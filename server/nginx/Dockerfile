FROM nginx:alpine

RUN apk update \
    && apk upgrade \
    && apk --update add logrotate \
    && apk add --no-cache openssl \
    && apk add --no-cache bash

# Create 'messages' file used from 'logrotate'
RUN touch /var/log/messages

# Copy 'logrotate' config file
COPY logrotate/nginx /etc/logrotate.d/

###########################################################################
# create nginx directories
###########################################################################

RUN rm -rf /etc/nginx/sites-available/* \
    && rm -rf /etc/nginx/sites-enabled/*

RUN mkdir -p /etc/nginx/sites-available/ && \
    mkdir -p /etc/nginx/sites-enabled/ && \
    mkdir -p /etc/nginx/ssl/ && \
    mkdir -p /etc/nginx/snippets/

###########################################################################
# create logs directories for each site
###########################################################################

RUN mkdir -p /var/log/nginx/site.local

###########################################################################
# copy over our nginx configurations
###########################################################################

COPY nginx.conf /etc/nginx/nginx.conf
COPY fastcgi-php.conf /etc/nginx/snippets
COPY fastcgi.conf /etc/nginx/fastcgi.conf
COPY fastcgi_params /etc/nginx/fastcgi_params

###########################################################################
# copy over our site development conf files
###########################################################################

COPY sites/site.local.conf /etc/nginx/sites-available

RUN ln -sf /etc/nginx/sites-available/site.local.conf /etc/nginx/sites-enabled/site.local.conf
