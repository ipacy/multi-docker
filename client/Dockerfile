FROM node:alpine

WORKDIR '/app'

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build
# /app/build <--- all the stuff
FROM nginx
# To expose port for the cloud (AWS)
EXPOSE 3000

COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

COPY --from=0 /app/build /usr/share/nginx/html