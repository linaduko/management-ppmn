FROM nginx:1.23.3-alpine

COPY ./config/nginx_int.conf /etc/nginx/conf.d/default.conf
COPY ./config/nginx_server.conf /etc/nginx/

RUN apk update \
    && apk upgrade \
    && apk add --no-cache curl \
    && apk add --no-cache openssl \
    && apk add --no-cache bash

RUN set -x; \
    addgroup -g 82 -S www-data; \
    adduser -u 82 -D -S -G www-data www-data && exit 0; exit 1

# For certificates
#COPY ./ssl/setup.sh /opt/setup.sh
#RUN sed -i 's/\r//g' /opt/setup.sh
#CMD ["/bin/bash", "/opt/setup.sh"]

EXPOSE 80 443
