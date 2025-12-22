FROM node:20-alpine

#Setting working directory
WORKDIR /usr/src/app

#Copying package.json
COPY package.json package-lock.json ./

#Installing dependencies from package-lock.json
RUN npm ci --omit=dev

#Copying all files
COPY . .

#Exposing 3000 to listen
EXPOSE 3000

#Starting the server
CMD ["node", "server.js"]