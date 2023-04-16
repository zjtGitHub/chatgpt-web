FROM node:16.18.0-alpine

RUN npm install pnpm -g

WORKDIR /app

COPY ./package.json /app

COPY ./pnpm-lock.yaml /app

RUN pnpm install

COPY . /app

RUN pnpm build

RUN pnpm install --production && \
    rm -rf /root/.npm /root/.pnpm-store /usr/local/share/.cache /tmp/*

COPY . /app

EXPOSE 3002

CMD ["pnpm", "run", "prod"]