FROM maven:3.8-openjdk-17 AS builder

WORKDIR /app
COPY pom.xml .
COPY src ./src

RUN mvn package -DskipTests

FROM openjdk:17-jdk-slim
WORKDIR /app
COPY --from=builder /app/target/*.jar app.jar

EXPOSE 8002
CMD ["java", "-jar", "app.jar"]