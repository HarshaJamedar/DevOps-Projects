# Stage 1: Build the application
FROM maven:3.9.4-eclipse-temurin-17 as build
WORKDIR /app

# Copy the Maven configuration and the pom.xml file first to leverage Docker cache
COPY pom.xml ./

# Download dependencies (using the pom.xml file) so that we can cache the dependencies in a separate layer
RUN mvn dependency:go-offline -B

# Now copy the rest of the application code and build the application
COPY src ./src

# Build the application
RUN mvn clean package -DskipTests

# Stage 2: Create a smaller image for running the application
FROM eclipse-temurin:17-jre as runtime
WORKDIR /app

# Copy the Spring Boot JAR from the build stage
COPY --from=build /app/target/weather-app-docker.jar /app/weather-app-docker.jar

# Expose port 8080 for the Spring Boot application
EXPOSE 8080

# Run the Spring Boot application
ENTRYPOINT ["java", "-jar", "/app/weather-app-docker.jar"]
