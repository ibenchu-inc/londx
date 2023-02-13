ARG NODE_VERSION=lts
FROM node:${NODE_VERSION}-alpine

ENV PM2=pm2-runtime
ENV LANG=C.UTF-8
# ARG ALPINE_GLIBC_BASE_URL="https://github.com/sgerrand/alpine-pkg-glibc/releases/download"
ARG ALPINE_GLIBC_PACKAGE_VERSION="2.35-r0"

## 使用国内时区，日志以中文显示

RUN wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub && \
    wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/"$ALPINE_GLIBC_PACKAGE_VERSION"/glibc-"$ALPINE_GLIBC_PACKAGE_VERSION".apk && \
    apk add glibc-"$ALPINE_GLIBC_PACKAGE_VERSION".apk 
    
RUN apk add --no-cache --virtual=.build-dependencies tzdata wget ca-certificates && \
    cp -r -f /usr/share/zoneinfo/Asia/Shanghai /etc/localtime 

RUN /usr/glibc-compat/bin/localedef --force --inputfile POSIX --charmap UTF-8 "$LANG" || true && \
    echo "export LANG=$LANG" > /etc/profile.d/locale.sh && \
    \
    apk del glibc-i18n && \
    \
    rm "/root/.wget-hsts" && \
    apk del .build-dependencies
   
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


RUN npm install pm2@latest -g && pm2 install typescript

WORKDIR /var/www/

EXPOSE 3000

CMD ["pm2-runtime", "npm","--","start"]


