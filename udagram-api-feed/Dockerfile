FROM node:14.15.0-alpine
WORKDIR /usr
COPY package.* ./
COPY tsconfig.json ./
COPY src ./src
RUN ls -a
RUN npm install
EXPOSE 8080
CMD ["npm","run","dev"]

