FROM node:lts AS build
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM nginx:1.23.3
WORKDIR /app
COPY --from=build /app/build .
COPY nginx.conf.template /etc/nginx/templates/default.conf.template
