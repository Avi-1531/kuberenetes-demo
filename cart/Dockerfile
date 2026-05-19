# so we ar edeceiding the node version via the package.json file but in this we dont have thi sdirectly mentione dthat it is using node 14 so we are seeing it via other package version are old so we have to take the node version also as old version
# ENV INSTANA_AUTO_PROFILE true thsi is used to enable the profiling we will learn it use in future
FROM node:14-alpine
WORKDIR /app
COPY package.json /app
RUN npm install
COPY server.js /app
EXPOSE 8080
CMD ["node","server.js"]