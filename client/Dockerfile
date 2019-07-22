FROM node:alpine as builder 
WORKDIR "/app" 
#This will create a file called build within the app directory
COPY ./package.json ./
RUN npm install
COPY . . 
RUN npm run build 

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
