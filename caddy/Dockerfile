FROM caddy:latest

WORKDIR /var/www

EXPOSE 80 443 2015

ENTRYPOINT ["caddy"]
CMD ["run", "--config", "/etc/Caddyfile"]
