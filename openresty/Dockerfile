FROM openresty/openresty:alpine-fat

COPY nginx.conf /usr/local/openresty/nginx/conf/
# sites /etc/nginx/conf.d/

RUN apk add --no-cache \
     openssl
RUN luarocks install lua-resty-auto-ssl && mkdir -p /etc/resty-auto-ssl/storage/file  
RUN set -x \
        && addgroup -g 82 -S www-data \
        && adduser -u 82 -D -S -G www-data www-data

RUN chown -R www-data:www-data /etc/resty-auto-ssl /var/log/nginx

RUN openssl req -new -newkey rsa:2048 -days 3650 -nodes -x509 \
      -subj '/CN=sni-support-required-for-valid-ssl' \
      -keyout /etc/ssl/resty-auto-ssl-fallback.key \
      -out /etc/ssl/resty-auto-ssl-fallback.crt && \
    openssl dhparam -out /etc/ssl/dhparam.pem 2048

WORKDIR /var/www

CMD [ "openresty","-g","daemon off;" ]

EXPOSE 80 443



