FROM maven AS builder
WORKDIR /opt/server
COPY pom.xml .
COPY src ./src
RUN mvn clean package


FROM eclipse-temurin:17-jre-alpine
ENV CART_ENDPOINT="cart:8080" \
    DB_HOST="mysql"
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
WORKDIR /opt/server
COPY --from=builder /opt/server/target/shipping-*.jar /opt/server/shipping.jar
RUN chown -R roboshop:roboshop /opt/server
USER roboshop
CMD ["java","-jar","shipping.jar"]





# FROM maven
# WORKDIR /opt/server/
# COPY pom.xml .
# COPY src ./src
# RUN mvn clean package
# RUN mv /opt/server/target/shipping-1.0.jar /opt/server/shipping.jar

# ENV CART_ENDPOINT="cart:8080" \
#     DB_HOST="mysql"

# CMD ["java", "-jar" , "shipping.jar"]