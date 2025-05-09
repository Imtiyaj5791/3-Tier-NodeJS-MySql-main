FROM node:latest AS Builder

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

RUN npm install terser-webpack-plugin@latest --save-dev

RUN npm start
RUN npm run build

FROM nginx:latest

EXPOSE 80

COPY --from=Builder /app/build /usr/share/nginx/html/
