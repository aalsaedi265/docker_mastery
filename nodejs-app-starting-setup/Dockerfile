# recgnize the node image from docker hub
FROM node

WORKDIR /app

# if were rebuilding this part will be checked by cache if it did not change which can save time
COPY package.json /app

RUN npm install

# dot tell to copy the file in this directory, second dot is the destination directory in the container container/nodejs-app-starting-setup
COPY . /app

EXPOSE 80

#use node command to run the server.js file
CMD ["node", "server.js"]