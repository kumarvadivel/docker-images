# Use Node.js LTS version as base image
FROM node:lts AS angular

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Copy the rest of the application source code
COPY . .

# Install dependencies
RUN npm install --force

# Build the Angular application
RUN npm run build

# Use Nginx as base image for serving the Angular application
FROM httpd:alpine3.15

WORKDIR /usr/local/apache2/htdocs
COPY --from=angular /app/dist/ .
