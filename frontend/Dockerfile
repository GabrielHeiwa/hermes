FROM node:18 as build 
WORKDIR /usr/src/app

COPY package*.json .

RUN npm install
COPY . .
RUN npm run build

FROM nginx:1.19
COPY ./config/nginx/nginx.conf /etc/nginx/nginx.conf
COPY --from=build /usr/src/app/build /usr/share/nginx/html
