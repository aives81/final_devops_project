FROM node:23-alpine AS build

WORKDIR /app

COPY . .

RUN yarn install
RUN yarn build
RUN mv .next/server/pages /app

FROM nginx:alpine

WORKDIR /app

COPY --from=build /app/ .

EXPOSE 3000

CMD ["yarn", "start"]

COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]