ARG NODE_VERSION=lts
FROM node:${NODE_VERSION}-alpine

# 常用环境变量
ARG NODE_ENV
ARG DB_POSTGRES_HOST
ARG DB_POSTGRES_PORT
ARG DB_REDIS_HOST
ARG DB_REDIS_PORT
ARG DB_POSTGRES
ARG DB_POSTGRES_DATABASE_SITE1
ARG DB_POSTGRES_DATABASE_SITE2
ARG DB_MYSQL
ARG DB_POSTGRES_DATABASE
ARG DB_POSTGRES_USERNAME
ARG DB_POSTGRES_PASSWORD

ENV NODE_ENV=${NODE_ENV} \
    DB_POSTGRES_HOST=${DB_POSTGRES_HOST} \
    DB_POSTGRES_PORT=${DB_POSTGRES_PORT} \
    DB_REDIS_HOST=${DB_REDIS_HOST} \
    DB_REDIS_PORT=${DB_REDIS_PORT} \
    DB_POSTGRES=${DB_POSTGRES} \
    DB_POSTGRES_DATABASE_SITE1=${DB_POSTGRES_DATABASE_SITE1} \
    DB_POSTGRES_DATABASE_SITE2=${DB_POSTGRES_DATABASE_SITE2} \
    DB_MYSQL=${DB_MYSQL} \
    DB_POSTGRES_DATABASE=${DB_POSTGRES_DATABASE} \
    DB_POSTGRES_USERNAME=${DB_POSTGRES_USERNAME} \
    DB_POSTGRES_PASSWORD=${DB_POSTGRES_PASSWORD}

ENV PM2=pm2-runtime
ENV LANG=C.UTF-8
# ARG ALPINE_GLIBC_BASE_URL="https://github.com/sgerrand/alpine-pkg-glibc/releases/download"
# ARG ALPINE_GLIBC_PACKAGE_VERSION="2.35-r0"

## 使用国内时区，日志以中文显示

# RUN wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub && \
#     wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/"$ALPINE_GLIBC_PACKAGE_VERSION"/glibc-"$ALPINE_GLIBC_PACKAGE_VERSION".apk && \
#     apk add glibc-"$ALPINE_GLIBC_PACKAGE_VERSION".apk 
    
# RUN apk add --no-cache --virtual=.build-dependencies tzdata wget ca-certificates && \
#     cp -r -f /usr/share/zoneinfo/Asia/Shanghai /etc/localtime 

# RUN /usr/glibc-compat/bin/localedef --force --inputfile POSIX --charmap UTF-8 "$LANG" || true && \
#     echo "export LANG=$LANG" > /etc/profile.d/locale.sh && \
#     \
#     apk del glibc-i18n && \
#     \
#     rm "/root/.wget-hsts" && \
#     apk del .build-dependencies
   
# RUN ALPINE_GLIBC_BASE_PACKAGE_FILENAME="glibc-$ALPINE_GLIBC_PACKAGE_VERSION.apk" && \
#     ALPINE_GLIBC_BIN_PACKAGE_FILENAME="glibc-bin-$ALPINE_GLIBC_PACKAGE_VERSION.apk" && \
#     ALPINE_GLIBC_I18N_PACKAGE_FILENAME="glibc-i18n-$ALPINE_GLIBC_PACKAGE_VERSION.apk" && \
#     apk add --no-cache --virtual=.build-dependencies tzdata wget ca-certificates && \
#     cp -r -f /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
#     wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub  && \
#     wget \
#         "$ALPINE_GLIBC_BASE_URL/$ALPINE_GLIBC_PACKAGE_VERSION/$ALPINE_GLIBC_BASE_PACKAGE_FILENAME" \
#         "$ALPINE_GLIBC_BASE_URL/$ALPINE_GLIBC_PACKAGE_VERSION/$ALPINE_GLIBC_BIN_PACKAGE_FILENAME" \
#         "$ALPINE_GLIBC_BASE_URL/$ALPINE_GLIBC_PACKAGE_VERSION/$ALPINE_GLIBC_I18N_PACKAGE_FILENAME" && \
#     apk add --no-cache \
#         "$ALPINE_GLIBC_BASE_PACKAGE_FILENAME" \
#         "$ALPINE_GLIBC_BIN_PACKAGE_FILENAME" \
#         "$ALPINE_GLIBC_I18N_PACKAGE_FILENAME" && \
#     \
#     rm "/etc/apk/keys/sgerrand.rsa.pub" && \
#     /usr/glibc-compat/bin/localedef --force --inputfile POSIX --charmap UTF-8 "$LANG" || true && \
#     echo "export LANG=$LANG" > /etc/profile.d/locale.sh && \
#     \
#     apk del glibc-i18n && \
#     \
#     rm "/root/.wget-hsts" && \
#     apk del .build-dependencies && \
#     rm \
#         "$ALPINE_GLIBC_BASE_PACKAGE_FILENAME" \
#         "$ALPINE_GLIBC_BIN_PACKAGE_FILENAME" \
#         "$ALPINE_GLIBC_I18N_PACKAGE_FILENAME"


# RUN yarn add pm2@latest -g && pm2 install typescript

WORKDIR /var/www/

EXPOSE 3000

CMD [ "npm","--","start"]


