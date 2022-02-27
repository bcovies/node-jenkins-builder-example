FROM node:14 AS nodebuild
WORKDIR /usr/src/app
# COPY package*.json ./
RUN npx create-react-app my-app
# COPY . .
RUN  cd ./my-app && npm run-script build
############################
FROM nginx:1.21.6 
WORKDIR /usr/share/nginx/html
COPY --from=nodebuild /usr/src/app/my-app/build ./
CMD ["nginx", "-g", "daemon off;"]