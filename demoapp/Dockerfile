# Stage 1: Build React App
FROM alpine:latest

ARG USERNAME=rashesh

WORKDIR /home/${USERNAME}/react-app

RUN apk add --update nodejs npm nginx bash

RUN adduser --gecos "$USERNAME" \
    --disabled-password \
    --shell /bin/sh \
    --uid 1001 \
    ${USERNAME}

COPY --chown=${USERNAME}:${USERNAME} . /home/${USERNAME}/app

COPY . /home/${USERNAME}/react-app

RUN npm install

# Expose port 8050

EXPOSE 8050

# Start nginx as the non-root user
USER ${USERNAME}

COPY nginx.conf etc/nginx/conf.d/default

# Start nginx
# CMD ["nginx", "-g", "daemon off;"]
CMD npm start
