# Use an official Maven image to build the application
FROM maven:3.8.6-openjdk-11 AS build
WORKDIR /app

# Copy source code
COPY . .

# Install dependencies and package the application while skipping tests
RUN mvn clean package -DskipTests

# Use a lightweight OpenJDK image for the final runtime
FROM openjdk:11-jre-slim
WORKDIR /app

# Copy the built JAR file from the build stage
COPY --from=build /app/target/users-api-0.0.1-SNAPSHOT.jar users-api.jar

# Command to run the application
CMD ["java", "-jar", "users-api.jar"]