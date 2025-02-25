FROM openjdk:17-jdk
WORKDIR /app
COPY target/users-api-0.0.1-SNAPSHOT.jar users-api.jar

EXPOSE 8081
CMD ["java", "-jar", "users-api.jar"]
