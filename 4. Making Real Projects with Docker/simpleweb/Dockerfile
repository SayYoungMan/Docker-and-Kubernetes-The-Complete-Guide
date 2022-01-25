# Specify a base image
FROM node:alpine

WORKDIR /usr/app

# Only require package.json for npm install
# Install dependencies
COPY ./package.json ./ 
RUN npm install

# Copy other files into container (this will stop unnecessary rebuild of image)
COPY ./ ./

# Default command
CMD [ "npm", "start" ]