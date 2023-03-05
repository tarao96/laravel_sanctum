FROM node:14

ARG ENV
ENV ENV $ENV

ENV HOST 0.0.0.0
EXPOSE 3000

#RUN npm install
#RUN mkdir /var/www/html
COPY ./front /var/www/html
COPY ./front/.env.${ENV} /var/www/html/.env

WORKDIR /var/www/html
RUN npm install

RUN npm run build

# サーバー起動
CMD npm run start