# creating lot of directories is because alpine image does not have the directories
# which nginx creates during its process run

FROM nginx:mainline-alpine3.20-slim
RUN rm -rf /etc/nginx/conf.d/* && \
    rm -rf /usr/share/nginx/html && \
    rm -rf /etc/nginx/nginx.conf && \
    apk add --no-cache libcap && \
    setcap 'cap_net_bind_service=+ep' /usr/sbin/nginx && \
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
COPY nginx.conf /etc/nginx/nginx.conf 
COPY expense.conf /etc/nginx/default.d/expense.conf
COPY code /usr/share/nginx/html 
EXPOSE 80
USER nginx
# Run in foreground
CMD ["nginx", "-g", "daemon off;"]