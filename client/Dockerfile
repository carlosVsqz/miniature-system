FROM node:9.11.1-alpine

RUN npm install -g http-server

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build


#FROM nginx:1.17.0-alpine
#
#COPY --from=build /app/build /var/www
#
#COPY nginx.conf /etc/nginx/nginx.conf
#

FROM nginx as production-stage
RUN mkdir /app
COPY --from=build-stage /app/dist /app
COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 80
ENTRYPOINT ["nginx","-g","daemon off;"]

