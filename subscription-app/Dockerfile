FROM node:16.13.1-alpine as build

WORKDIR /app3

COPY package.json .

RUN npm install

COPY . /app3

RUN npm run build

#CMD ["npm","start"]



FROM nginx:1.19.0-alpine

EXPOSE 3000

COPY --from=build /app3/dist /usr/share/nginx/html

COPY --from=build /app3 /usr/share/nginx/html

COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

