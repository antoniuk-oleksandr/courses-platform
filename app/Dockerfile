FROM node:24.5-alpine

WORKDIR /usr/src/app

RUN corepack enable && corepack prepare pnpm@latest --activate

COPY package.json pnpm-lock.yaml* ./

RUN pnpm install --prod && \
    pnpm add @prisma/client

COPY . .

RUN pnpm run build

EXPOSE 8080

CMD ["node", "dist/src/main.js"]