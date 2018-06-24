FROM openresty/openresty:alpine-fat

ARG NODE_VERSION=8.x
#COPY sites /etc/nginx/conf.d/

# RUN cd /etc/nginx && ls

# RUN cd /usr/local/openresty/nginx/conf  && cat nginx.conf

# RUN apk add --no-cache \
#     openssl

RUN apk add --no-cache \
    openssl

RUN luarocks install lua-resty-auto-ssl && mkdir /etc/resty-auto-ssl

RUN openssl req -new -newkey rsa:2048 -days 3650 -nodes -x509 \
      -subj '/CN=sni-support-required-for-valid-ssl' \
      -keyout /etc/ssl/resty-auto-ssl-fallback.key \
      -out /etc/ssl/resty-auto-ssl-fallback.crt && \
    openssl dhparam -out /etc/nginx/ssl/dhparam.pem 2048

WORKDIR /var/www

CMD [ "openrsty" ]