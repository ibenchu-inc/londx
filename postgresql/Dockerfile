FROM postgres:alpine

RUN apk add --no-cache --virtual=.build-dependencies tzdata wget ca-certificates && \
    cp -r -f /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

CMD ["postgres"]

EXPOSE 5432
