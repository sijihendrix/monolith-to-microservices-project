# FROM node:14.15.0-alpine
# WORKDIR /usr
# COPY package.* ./
# COPY tsconfig.json ./
# COPY src ./src
# RUN ls -a
# RUN npm install
# EXPOSE 8080
# CMD ["npm","run","dev"]

FROM node:14.15.0-alpine
# Create app directory
WORKDIR /usr/src/app
# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied where available (npm@5+)
COPY package*.json ./
RUN npm ci 
# Bundle app source
COPY . .
EXPOSE 8080
CMD [ "npm", "run", "prod" ]
