Nome directory: mybook

Descrizione: all'interno di un pc veniva installata tramite il software di virtualizzazione vmware una macchina virtuale con sistema operativo ubuntu server,
contenente un profilo "gruppo4" dove veniva installato docker, il cui scopo è quello di creare dei container.

(Dockerfile)
FROM node:15.13-alpine
WORKDIR /mybook
ENV PATH="./node_modules/.bin:$PATH"
COPY . .
RUN npm run build
CMD ["npm","start"]

(docker-compose.yml)
version: "3.8"
services:
  app:
    build:
      context: .
    volumes:
      - .:/mybook
    ports:
      - 3000:3000
    image: app:react 
    container_name: react_container 
    command: npm start
  

