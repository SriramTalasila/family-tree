# Stage 1: Build the application
FROM maven:3.9.8-eclipse-temurin-21 AS build

# Set the working directory in the container
WORKDIR /app

# Copy the pom.xml and source code
COPY pom.xml .
COPY src ./src

# Package the application
RUN mvn clean install -DskipTests

# Stage 2: Run the application
FROM eclipse-temurin:21-jdk-alpine

# Set the working directory in the container
WORKDIR /app

# Copy the jar file from the previous stage
COPY --from=build /app/target/*.jar /app/demo.jar

# Expose the port that the application runs on
EXPOSE 8085

# Run the jar file
ENTRYPOINT ["java", "-jar", "/app/demo.jar"]
