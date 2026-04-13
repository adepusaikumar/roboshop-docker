FROM 20.20.2-alpine3.23 AS builder
# this creates /app and move there
WORKDIR /app
COPY package.json .
COPY *.js .
RUN npm install

FROM 20.20.2-alpine3.23
WORKDIR /app
COPY --from=builder /app /app
ENV REDIS_HOST="redis" \
    CATALOGUE_HOST="catalogue" \
    CATALOGUE_PORT="8080"
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
RUN chown -R roboshop:roboshop /app
USER roboshop
CMD ["server.js"]
ENTRYPOINT [ "node" ]

# FROM node:20.0
# # this creates /app and move there
# WORKDIR /app
# COPY * .
# RUN npm install
# ENV REDIS_HOST="redis" \
#     CATALOGUE_HOST="catalogue" \
#     CATALOGUE_PORT="8080"
# EXPOSE 8080
# CMD ["node", "server.js"]