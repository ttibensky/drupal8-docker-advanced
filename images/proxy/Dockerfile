FROM nginx

# Remove default nginx site configuration.
RUN rm -rf /etc/nginx/conf.d/default.conf

# Add nginx proxy configuration.
COPY nginx-proxy.conf /etc/nginx/conf.d/proxy.conf

# Run nginx in foreground.
CMD ["nginx", "-g", "daemon off;"]
