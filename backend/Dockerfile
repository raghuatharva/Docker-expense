# dockerfile before best practises


FROM node:20
ENV DB_HOST=mysql
RUN mkdir -p /app
EXPOSE 8080
WORKDIR /app
COPY *.js .
COPY package.json .
RUN npm install
CMD [ "node", "index.js" ]

# DB_host=mysql ; this is the main connecting point from backend to mysql; without this the data wont flow
# to mysql -- why DB_HOST has to be taken as variable is ; in the .js files ,
# the code tells that " it will read DB_HOST for database URL"