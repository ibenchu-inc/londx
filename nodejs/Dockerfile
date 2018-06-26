ARG NODE_VERSION=latest
FROM node:${NODE_VERSION}-alpine

RUN npm install pm2@latest -g 

WORKDIR /var/www/

EXPOSE 3000-6000

CMD ["pm2-runtime", "process.yml"]