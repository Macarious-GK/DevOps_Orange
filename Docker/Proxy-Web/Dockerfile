# Use the official NGINX base image
FROM nginx:latest

# Copy custom NGINX configuration to the container
COPY nginx.conf /etc/nginx/nginx.conf

# Expose port 80
EXPOSE 80

# Start NGINX
CMD ["nginx", "-g", "daemon off;"]
