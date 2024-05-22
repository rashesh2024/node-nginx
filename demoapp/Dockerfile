# Stage 1: Build React App
FROM alpine:latest

RUN apk add --update nodejs npm nginx bash

RUN addgroup -S && appgroup -S -G appgroup -s bin/sh rashesh

RUN -p /var/run/nginx &&\
    touch var/run/nginx.pid && \
    chown -R rashesh:appgroup var/run/nginx var/log/nginx var/lib/nginx etc/nginx var/run/nginx.pid

COPY nginx.conf etc/nginx/nginx.conf

WORKDIR /home/rashesh/react-app

COPY --chown=rashesh:appgroup . .

RUN npm install

EXPOSE 8050

# Start nginx as the non-root user
USER rashesh


CMD [ "sh" ,"-c",  "nginx && node index.js" ]