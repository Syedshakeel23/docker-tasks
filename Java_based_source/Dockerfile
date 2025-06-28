# Stage 1: Build the application using Maven
FROM maven:3.8.7-eclipse-temurin-11 AS build
MAINTAINER SYED_SHAKEEL

# Set working directory inside container
WORKDIR /app

# Copy the Maven project files into the container
COPY pom.xml .
COPY src ./src

# Package the application (creates target/spring-boot-web.jar)
RUN mvn clean package -DskipTests

# Stage 2: Run the built jar using a lightweight JDK image
FROM eclipse-temurin:11-jre-alpine

# Set working directory
WORKDIR /app

# Copy built jar file from the build stage
COPY --from=build /app/target/spring-boot-web.jar app.jar

# Expose application port (default Spring Boot port)
EXPOSE 8080

# Run the application
ENTRYPOINT ["java", "-jar", "app.jar"]

