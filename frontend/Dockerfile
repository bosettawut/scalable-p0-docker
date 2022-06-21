FROM node:16 as builder

CMD mkdir /app

# set the working directory
WORKDIR /app 

# copy all dependencies in app directory
COPY /scalable-ums-frontend/package.json /scalable-ums-frontend/yarn.lock ./

# install all dependencies in app
RUN yarn install

# copy all file to app
COPY /scalable-ums-frontend ./

RUN yarn build

FROM nginx:alpine
COPY --from=builder /app/dist /usr/share/nginx/html/
EXPOSE 80
# CMD ["nginx","-g","daemon off;"]

