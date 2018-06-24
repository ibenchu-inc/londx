FROM openresty/openresty:alpine-fat

ARG NODE_VERSION=8.x
#COPY sites /etc/nginx/conf.d/

# RUN cd /etc/nginx && ls

# RUN cd /usr/local/openresty/nginx/conf  && cat nginx.conf

# RUN apk add --no-cache \
#     openssl

RUN apk add --no-cache \
    openssl \

RUN luarocks install lua-resty-auto-ssl

WORKDIR /var/www

CMD [ "openrsty" ]