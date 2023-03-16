VERSION 0.7
FROM node:16.13.1
WORKDIR /usr/src/react-app

deps:
    COPY package.json ./
    COPY package-lock.json ./
    COPY . .
    RUN npm install
    # Output these back in case npm install changes them.
    SAVE ARTIFACT package.json AS LOCAL ./package.json
    SAVE ARTIFACT package-lock.json AS LOCAL ./package-lock.json

build:
    FROM +deps
    RUN npm run build
    
docker:
    FROM +deps
    COPY +build/build ./build
    EXPOSE 8080