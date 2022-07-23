FROM node:16.13.1-alpine as build

WORKDIR /app3

COPY package.json .

RUN npm install -g npm@8.14.0

RUN npm install

COPY . /app3

RUN npm run build

#CMD ["npm","start"]



FROM nginx:1.19.0-alpine

COPY --from=build /app3/dist /usr/share/nginx/html

COPY default.conf /etc/nginx/conf.d/default.conf

CMD ["nginx","-g","daemon off;"]
