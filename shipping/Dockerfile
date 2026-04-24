FROM maven AS builder
WORKDIR /opt/server
COPY pom.xml .
COPY src /opt/server/src
RUN mvn clean package \
    && mv /opt/server/target/shipping-1.0.jar /opt/server/shipping.jar

FROM eclipse-temurin:17-jre-alphine
EXPOSE 8080
WORKDIR /opt/server
RUN addgroup -S electronic-shop && adduser -S electronic-shop -G electronic-shop
ENV CART_ENDPOINT="cart:8080" \
    DB_HOST="mysql"
COPY --from=builder /opt/server/target/shipping-*.jar /opt/server/shipping.jar
USER electronic-shop
CMD ["java", "-jar", "shipping.jar"]