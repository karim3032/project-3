## Build stage
FROM beevelop/ionic:v2021.06.1 AS build
# Create app directory
WORKDIR /usr/src/app
# Install app dependencies
COPY package*.json ./
RUN npm ci
# Bundle app source
COPY . .
RUN ionic build

## Run stage
FROM nginx:alpine
# Copy the built artifacts from the build stage
COPY --from=build /usr/src/app/www /usr/share/nginx/html