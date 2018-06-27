ARG NODE_VERSION=${NODE_VERSION}
FROM node:${NODE_VERSION}-stretch
### IF you from china###
RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak && \
    echo "deb http://mirrors.163.com/debian/ stretch main non-free contrib" >/etc/apt/sources.list && \
    echo "deb http://mirrors.163.com/debian/ stretch-proposed-updates main non-free contrib" >>/etc/apt/sources.list && \
    echo "deb-src http://mirrors.163.com/debian/ stretch main non-free contrib" >>/etc/apt/sources.list && \
    echo "deb-src http://mirrors.163.com/debian/ stretch-proposed-updates main non-free contrib" >>/etc/apt/sources.list

RUN npm set registry https://registry.npm.taobao.org && \
    npm set disturl https://npm.taobao.org/dist && \
    npm set sass_binary_site https://npm.taobao.org/mirrors/node-sass

RUN npm install pm2@latest -g 

WORKDIR /var/www/