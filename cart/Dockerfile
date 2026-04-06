FROM node:20.0
# this creates /app and move there
WORKDIR /app
COPY * .
RUN npm install
ENV REDIS_HOST="redis" \
    CATALOGUE_HOST="catalogue" \
    CATALOGUE_PORT="8080"
EXPOSE 8080
CMD ["node", "server.js"]