ARG NODE_VERSION=latest
FROM node:${NODE_VERSION}-alpine

ENV PM2=pm2-runtime

## 使用国内时区
RUN apk --no-cache add tzdata ca-certificates && \
    cp -r -f /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
    
## 解决日志中文乱码问题

RUN echo "export LANG=zh_CN.utf8" >> /home/tomcat/.bash_profile
    
RUN npm install pm2@latest -g 

WORKDIR /var/www/

EXPOSE 3000-6000

CMD ["pm2-runtime", "npm","--","start"]


