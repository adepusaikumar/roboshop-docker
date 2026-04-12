FROM node:20.0
# this creates /app and move there
WORKDIR /app
COPY * .
RUN npm install
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
CMD ["node", "server.js"]