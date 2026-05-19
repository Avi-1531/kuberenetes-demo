FROM node:14

ENV INSTANA_AUTO_PROFILE true

EXPOSE 8080

WORKDIR /app

COPY package.json /app

RUN npm install

COPY server.js /app

CMD ["node", "server.js"]

