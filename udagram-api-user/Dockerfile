FROM node:14.15.0-alpine

ENV POSTGRES_USERNAME=postgres
ENV POSTGRES_PASSWORD=flXpF2Ac8diYOqpl5gNN
ENV POSTGRES_HOST=database-1.c6sllbwmtjf3.us-east-1.rds.amazonaws.com
ENV POSTGRES_DB=postgres
ENV AWS_BUCKET=arn:aws:s3:::udagram-s3-12212
ENV AWS_REGION=us-east-1
ENV AWS_PROFILE=default
ENV JWT_SECRET=testing
ENV URL=http://localhost:8100
WORKDIR /usr
COPY package.* ./
COPY tsconfig.json ./
COPY src ./src
RUN ls -a
RUN npm install
EXPOSE 8080
CMD ["npm","run","dev"]

