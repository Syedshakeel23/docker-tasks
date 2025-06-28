# Use official nginx image as base
FROM nginx:alpine

# Set working directory
WORKDIR /usr/share/nginx/html

# Remove default nginx index page
RUN rm -rf ./*

# Copy your static files into the container
COPY index.html .
COPY style.css .
COPY javascript.js .
COPY todayDeal.js .

# Expose port 80 for HTTP traffic
EXPOSE 80

# Start nginx (default command from base image works)

