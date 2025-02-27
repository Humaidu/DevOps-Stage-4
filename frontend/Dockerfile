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

# Use a lightweight Node.js runtime for serving the app
FROM node:14-alpine

# Set the working directory inside the container
WORKDIR /app

# Install a simple static file server (serve)
RUN npm install -g serve

# Copy built frontend files from the previous stage
COPY --from=build /app/dist .

# Expose the application port
EXPOSE 8080

# Start the app using "serve"
CMD ["serve", "-s", ".", "-l", "8080"]
