# 使用官方 builder 镜像构建带 git 插件的 caddy
FROM caddy:builder AS builder
RUN xcaddy build --with github.com/abiosoft/caddy-git

FROM caddy:latest
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories && \
    apk --no-cache add git openssh-client
COPY --from=builder /usr/bin/caddy /usr/bin/caddy

WORKDIR /var/www

EXPOSE 80 443 2015

ENTRYPOINT ["caddy"]
CMD ["run", "--config", "/etc/Caddyfile"]