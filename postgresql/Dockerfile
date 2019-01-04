ARG PG_VERSION=latest
FROM postgres:${PG_VERSION}-alpine

RUN apk add --no-cache --virtual=.build-dependencies tzdata ca-certificates && \
    cp -r -f /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    apk del .build-dependencies
    

CMD ["postgres"]

EXPOSE 5432
