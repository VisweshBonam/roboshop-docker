FROM node:20

WORKDIR /opt/serever
COPY package.json /opt/server
COPY *.js /opt/serever

RUN npm install

ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"

CMD ["node", "server.js"]