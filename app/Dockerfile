FROM node:18-alpine as build

WORKDIR /src

COPY package.json yarn.lock ./
RUN yarn install
COPY . .

RUN yarn build

FROM nginx:alpine
COPY --from=build /src/dist /usr/share/nginx/html
EXPOSE 80