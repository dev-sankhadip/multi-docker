FROM node:19-alpine3.16 AS builder
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .

RUN npm run build

FROM ngnix
EXPOSE 3000
COPY ./nginx/default.conf /etc/ngnix/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html