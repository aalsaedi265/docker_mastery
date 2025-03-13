
FROM node

ARG Default_port = 80

WORKDIR /app

COPY package.json /app

RUN npm install

COPY . /app

#ENV PORT $Default_port

EXPOSE 80

#folder in containter, app, which will later be linked to folder outside 
VOLUME [ "/app/feeback" ]

CMD ["node", "server.js"]