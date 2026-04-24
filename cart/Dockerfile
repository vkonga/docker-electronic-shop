FROM node:20-alphine3.21 AS builder
WORKDIR /opt/server
COPY package.json .
COPY *.js .
RUN npm install

FROM node:20-alphine3.21
RUN addgroup -S electronic-shop && adduser -S electronic-shop -G electronic-shop
ENV REDIS_HOST="true" \
    CATALOGUE_HOST="catalogue" \
    CATALOGUE_PORT="8080"
WORKDIR /opt/server
USER electronic-shop
COPY --from=builder /opt/server /opt/server
CMD ["node","server.js"]