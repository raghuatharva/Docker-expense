
# Use valid official image
FROM nginx:mainline-alpine3.20-slim


# Set permissions (secure config, allow HTML access) google it !!! dont worry about itdocke
# Set permissions (secure config, allow HTML access)
RUN rm -rf /etc/nginx/conf.d/* && \
    rm -rf /usr/share/nginx/html && \
    rm -rf /etc/nginx/nginx.conf && \
    mkdir -p /var/cache/nginx/client_temp && \
    mkdir -p /var/cache/nginx/proxy_temp && \
    mkdir -p /var/cache/nginx/fastcgi_temp && \
    mkdir -p /var/cache/nginx/uwsgi_temp && \
    mkdir -p /var/cache/nginx/scgi_temp && \
    chown -R nginx:nginx /var/cache/nginx && \
    chown -R nginx:nginx /etc/nginx/ && \
    chmod -R 755 /etc/nginx/ && \
    chown -R nginx:nginx /var/log/nginx && \
    touch /var/run/nginx.pid && \
    chown -R nginx:nginx /var/run/nginx.pid /run/nginx.pid

# Copy custom config and static files
COPY nginx.conf /etc/nginx/nginx.conf 
COPY expense.conf /etc/nginx/default.d/expense.conf
COPY code /usr/share/nginx/html 

# Expose port and healthcheck
EXPOSE 80

# Switch to non-root user
USER nginx

# Run in foreground
CMD ["nginx", "-g", "daemon off;"]