FROM node:20.0
# this creates /app and move there
WORKDIR /app
COPY * .
RUN npm install
ENV MONGO="true" \
    REDIS_URL="redis://redis:6379" \
    MONGO_URL="mongodb://mongodb:27017/users"
EXPOSE 8080
CMD ["node", "server.js"]