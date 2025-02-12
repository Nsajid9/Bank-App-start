# First stage: Build the application
FROM maven:3-eclipse-temurin-21 AS build

WORKDIR /app
COPY . .  
RUN mvn clean package -DskipTests

# Second stage: Run the application
FROM openjdk:21-alpine  # Using OpenJDK as an alternative

WORKDIR /app
COPY --from=build /app/target/*.jar bankapp.jar  

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "bankapp.jar"]
