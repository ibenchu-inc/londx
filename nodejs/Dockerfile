ARG NODE_VERSION=latest
FROM node:${NODE_VERSION}-alpine

ENV PM2=pm2-runtime

## 使用国内时区
RUN apk --no-cache add tzdata ca-certificates && \
    cp -r -f /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
    
RUN npm install pm2@latest -g 

WORKDIR /var/www/

EXPOSE 3000-6000

# ENTRYPOINT [ "sh", "-c", "$PM2 start" ]

#CMD ["sh","-c","$PM2 start npm -- start"]
CMD ["pm2-runtime", "npm","--","start"]

# CMD ["npm -- start"]

