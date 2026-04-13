FROM node:20.20.2-alpine3.23 AS builder
# this creates /app and move there
WORKDIR /app
COPY * .
RUN npm install

FROM node:20.20.2-alpine3.23
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
RUN chown -R roboshop:roboshop /app
USER roboshop
EXPOSE 8080
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
CMD ["server.js"]
ENTRYPOINT [ "node" ]

# FROM node:20.0
# # this creates /app and move there
# WORKDIR /app
# COPY * .
# RUN npm install
# ENV MONGO="true" \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD ["node", "server.js"]