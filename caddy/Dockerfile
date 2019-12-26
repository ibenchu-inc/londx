FROM abiosoft/caddy

WORKDIR /var/www

EXPOSE 80 443 2015

ENTRYPOINT ["/bin/parent", "caddy"]
#CMD ["--conf", "/etc/Caddyfile", "-quic","--log", "stdout", "--agree=true"]

CMD ["--conf", "/etc/Caddyfile","--log", "stdout", "--agree=true"]
