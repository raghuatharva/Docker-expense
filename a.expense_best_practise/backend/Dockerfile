# Key Benefits of Multi-Stage Build

#  Smaller Image Size – The final image doesn’t include unnecessary
#        build dependencies (e.g., npm cache, extra packages)
#  Improved Security – Runs as a non-root user (raghu) instead of root
#  Better Performance – The image loads faster and runs efficiently

FROM node:20 AS builder
RUN mkdir -p /app
WORKDIR /app
COPY package.json .
COPY *.js .
RUN npm install


FROM node:20.18.0-alpine3.20
EXPOSE 8080
ENV DB_HOST=mysql
RUN addgroup -S expense && adduser -S raghu -G expense  && \
    mkdir -p /app && \
    chown -R raghu:expense /app 
WORKDIR /app
COPY --from=builder /app /app
USER raghu
CMD ["node","index.js"]

# NOW RAGHU becomes the owner of /app, even though he's not root USER.
# He can read/write/run in /app as it's owned by him.

# 💡 Real-world use:
# Non-root user owns the app directory → safer containers 🔐







# FROM node:20
# ENV DB_HOST=mysql
# RUN mkdir -p /app
# EXPOSE 8080
# WORKDIR /app
# COPY *.js .
# COPY package.json .
# RUN npm install
# CMD [ "node", "index.js" ]

# DB_host=mysql ; this is the main connecting point from backend to mysql; without this the data wont flow
# to mysql -- why DB_HOST has to be taken as variable is ; in the .js files ,
# the code tells that " it will read DB_HOST for database URL"