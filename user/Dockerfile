FROM node:20-alpine3.21
WORKDIR /opt/server
COPY package.json /opt/server
COPY *.js /opt/server

RUN npm install 

ENV MONGO="true" \
    REDIS_URL="redis://redis:6379" \
    MONGO_URL="mongodb://mongodb:27017/users"

CMD ["node", "server.js"]
    