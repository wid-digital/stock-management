# Use the official Node.js runtime as the base image
FROM node:18-alpine

# Set the working directory inside the container
WORKDIR /app

# Copy the package.json and package-lock.json files into the container
COPY package*.json ./

# Install the project dependencies
RUN npm install

# Copy the application source code into the container
COPY . .

# Build the Angular app
RUN npm run build --prod

# Use Nginx to serve the Angular app
FROM nginx:latest

# Copy the built Angular app to the Nginx HTML folder
COPY --from=0 /app/dist/frontend /usr/share/nginx/html

# Expose the port for Nginx
EXPOSE 80
