ARG PG_VERSION=latest
FROM postgres:${PG_VERSION}-alpine

# 常用环境变量
ARG DB_POSTGRES_DATABASE
ARG DB_POSTGRES_USERNAME
ARG DB_POSTGRES_PASSWORD

ENV POSTGRES_DB=${DB_POSTGRES_DATABASE} \
    POSTGRES_USER=${DB_POSTGRES_USERNAME} \
    POSTGRES_PASSWORD=${DB_POSTGRES_PASSWORD}

RUN apk add --no-cache --virtual=.build-dependencies tzdata ca-certificates && \
    cp -r -f /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    apk del .build-dependencies
    

CMD ["postgres"]

EXPOSE 5432
