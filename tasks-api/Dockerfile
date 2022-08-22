FROM node:14-alpine

ENV appname tasks

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 8000

CMD [ "node", "tasks-app.js" ]