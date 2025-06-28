# Use an official Node.js image as base
FROM node:18-alpine as build
MAINTAINER SYED_SHAKEEL

# Set working directory
WORKDIR /app

# Copy package files first (to leverage Docker cache)
COPY package*.json ./

# Install project dependencies
RUN npm install

# Copy all source code to working directory
COPY . .

# Build the React app for production
RUN npm run build

# Use nginx for serving the built app
FROM nginx:alpine

# Copy built files from previous stage to nginx html directory
COPY --from=build /app/build /usr/share/nginx/html

# Expose port 80
EXPOSE 80

# Start nginx when container launches
CMD ["nginx", "-g", "daemon off;"]

