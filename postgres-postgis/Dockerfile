ARG POSTGIS_VERSION=latest
FROM postgis/postgis:${POSTGIS_VERSION}

RUN apk add --no-cache --virtual=.build-dependencies tzdata ca-certificates && \
    cp -r -f /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    apk del .build-dependencies
    
EXPOSE 5432

CMD ["postgres"]


