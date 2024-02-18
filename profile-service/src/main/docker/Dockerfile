FROM maven:3.8.4-jdk-8-slim AS build

WORKDIR /app

COPY . /app


COPY pom.xml .
COPY src ./src

RUN mvn clean package

FROM openjdk:8-jdk-alpine
WORKDIR /app

COPY --from=build /app/target/*.jar /app/profile-service.jar

EXPOSE 8080

CMD ["java", "-jar", "profile-service.jar"]
