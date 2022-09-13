# Build
FROM beevelop/ionic:latest AS ionic
# Create app directory
WORKDIR /usr/src/app
# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./
RUN npm install -f
# Bundle app source
COPY . .
RUN ionic build
## Run 
FROM nginx:alpine
#COPY www /usr/share/nginx/html
COPY --from=ionic  /usr/src/app/www /usr/share/nginx/html


# FROM node:14.15.0-alpine

# FROM node:14.15.0-alpine as build
# WORKDIR /app
# COPY package*.json /app/
# RUN npm install -g ionic
# RUN npm install -f
# COPY ./ /app/
# RUN npm run-script build:prod
# FROM nginx:alpine
# RUN rm -rf /usr/share/nginx/html/*
# COPY --from=build /app/www/ /usr/share/nginx/html/