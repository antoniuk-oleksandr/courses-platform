FROM node:24.5-alpine

WORKDIR /usr/src/app

RUN corepack enable && corepack prepare pnpm@latest --activate

COPY package.json pnpm-lock.yaml* ./

RUN pnpm install --frozen-lockfile --prod && \
    pnpm add @prisma/client

COPY prisma/schema.prisma ./prisma/

RUN npx prisma generate

COPY . .

RUN pnpm run build

EXPOSE 8080

CMD ["node", "dist/main.js"]