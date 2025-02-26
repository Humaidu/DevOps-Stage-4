# Use an official Node.js runtime as the base image for building
FROM node:14 AS build

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json first to take advantage of Docker cache
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application source code
COPY . .

# Build the application
RUN npm run build

# Use an Nginx image to serve the static files
FROM nginx:alpine

# Set working directory to Nginx default path
WORKDIR /usr/share/nginx/html

# Remove the default Nginx static files
RUN rm -rf ./*

# Copy built frontend files from the previous stage
COPY --from=build /app/dist .

# Expose the default Nginx HTTP port
EXPOSE 80

# Start Nginx when the container runs
CMD ["nginx", "-g", "daemon off;"]


