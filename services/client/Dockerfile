FROM node:20-alpine

RUN apk add --no-cache tini

RUN mkdir -p /var/www/client

RUN chown -R node:node /var/www/client

USER node

WORKDIR /var/www/client

COPY --chown=node:node client/package*.json ./

ENV HOST 0.0.0.0

RUN npm install

RUN npm cache clean --force

ENTRYPOINT ["/sbin/tini", "--"]

CMD ["npm", "run", "dev"]
