### Define where to get the build image from on DockerHub and name image as builder
FROM node:alpine as builder

### Set the working directory on the container
WORKDIR '/app'

### Copy the local package.json to the WORKDIR on the container
COPY ./package.json ./

### Run npm install on the container
RUN npm install

### Copy the remaining files/directories from local directory to the container working directory
COPY . .

### Set up production build process by running NPM RUN BUILD
RUN npm run build

#########################################################
### NEXT BUILD
#########################################################
### Define where to get the build image from on DockerHub for nginx
FROM nginx

### Expose port 3000
EXPOSE 3000

### Overwrite container default.conf with local copy
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf