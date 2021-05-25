#Phase 1 - building
# FROM node:alpine

#If I wanted to tag this with a different name:
FROM node:alpine as builder

WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . .
RUN npm run build 
#build folder will be created in the build dir /app/build

#Phase 2 - running
FROM nginx
COPY --from=builder /app/build /usr/share/nginx/html
#default command of nginx is to start the container, so does not need to be declared here

#summary: phase 1 results in the build directory. That is all we need.
#phase 2 just runs nginx which will use that build dir for its operation.
#all of the unecessary waste generated in phase 1 is not used.