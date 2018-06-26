FROM abiosoft/caddy

WORKDIR /var/www

EXPOSE 80 443 2015

ENTRYPOINT ["/bin/parent", "caddy"]
CMD ["--conf", "/etc/Caddyfile", "--log", "stdout", "--agree=$ACME_AGREE"]