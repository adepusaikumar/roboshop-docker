FROM maven:3.9.14 AS builder
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package
RUN mv target/shipping-1.0.jar shipping.jar

FROM eclipse-temurin:17-jre-alpine
WORKDIR /app
RUN addgroup -S roboshop && adduser -SG roboshop roboshop
RUN chown -R roboshop:roboshop /app
USER roboshop
COPY --from=builder /app/shipping.jar .
EXPOSE 8080
ENV CART_ENDPOINT="cart:8080" \
    DB_HOST="mysql"
    
CMD ["shipping.jar"]
ENTRYPOINT [ "java", "-jar"]

# FROM maven:3.9.14
# EXPOSE 8080
# WORKDIR /app
# COPY pom.xml .
# COPY src ./src
# RUN mvn clean package
# RUN mv target/shipping-1.0.jar shipping.jar 
# ENV CART_ENDPOINT="cart:8080" \
#     DB_HOST="mysql"
# CMD ["java", "-jar", "shipping.jar"]