FROM node:12-alpine AS build

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

FROM nginx:stable

COPY --from=build /usr/src/app/public /var/www

CMD ["nginx", "-g", "daemon off;"]