# dockerfile before best practises


FROM nginx
RUN rm -rf /usr/share/nginx/html
COPY /code/ usr/share/nginx/html
RUN rm -rf /etc/nginx/conf.d/default.conf
RUN rm -rf /etc/nginx/nginx.conf
COPY nginx.conf /etc/nginx/nginx.conf
COPY expense.conf /etc/nginx/default.d/expense.conf
CMD ["nginx", "-g", "daemon off;"]


# 👤 You: "Yo NGINX, what's with -g daemon off;?"
# 🖥️ NGINX: "Oh that? That just tells me not to run in the background like I usually do."
# 👤 You: "Why would anyone wanna do that?"
# 🛠️ NGINX: "Well, mostly for Docker and containers, bro. In containers, the main process must run in the foreground — otherwise, the container thinks it's done and shuts down."