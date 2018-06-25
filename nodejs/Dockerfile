ARG NODE_VERSION=${NODE_VERSION}
FROM node:${NODE_VERSION}-alpine

RUN npm install pm2@latest -g 

WORKDIR /var/www

RUN echo -e "apps: \n\
  - script   : app.js \n\
    instances: 2  \n\
    exec_mode: cluster" >> process.yml


EXPOSE 3000-4000

CMD ["pm2-runtime", "start", "process.yml"]