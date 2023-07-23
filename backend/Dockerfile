# # Use an OpenJDK runtime as the base image
# FROM khipu/openjdk17-alpine

# # Set the working directory inside the container
# WORKDIR /app

# # Copy the JAR file into the container
# # COPY target/*.jar app.jar
# COPY target/demo*.jar app.jar

# # Expose the port your Spring Boot app is listening on
# EXPOSE 8080

# # Set the command to run the Spring Boot application
# CMD ["java", "-jar", "app.jar"]

# Stage 1: Build the application
FROM adoptopenjdk/openjdk11:alpine AS build
WORKDIR /app
COPY . .
RUN ./mvnw package -DskipTests

# Stage 2: Create the final image
FROM adoptopenjdk/openjdk11:alpine-jre
WORKDIR /app
COPY --from=build /app/target/demo.jar app.jar
EXPOSE 8080
CMD ["java", "-jar", "app.jar"]
