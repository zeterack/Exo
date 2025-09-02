FROM nginx:alpine

# Copy custom HTML files into the nginx web root
COPY ./html /usr/share/nginx/html

# Expose port 80
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]
