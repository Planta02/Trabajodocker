FROM node:20

USER root

RUN apt-get update && apt-get install -y \
    wget \
    nano

RUN npm cache clean --force

RUN npm install -g npm@8.12.1

RUN npm install prisma -g\
    && npm i cors -g \
    && npm i dotenv -g \
    && npm i express -g \
    && npm i jsonwebtoken -g \
    && npm i nodemon -g \
    && npm i @prisma/client -g

RUN mkdir -p /srv/serverAPI/

WORKDIR /srv/serverAPI/

COPY server/package*.json /srv/serverAPI/

RUN npm install

RUN npm install dotenv --save-dev

COPY server/ /srv/serverAPI/
RUN prisma generate

CMD ["nodemon", "index.js"]