
FROM maven:3-eclipse-temurin-21 AS build

WORKDIR /app
COPY . .  
RUN mvn clean package -DskipTests


FROM openjdk:21-alpine  

WORKDIR /app
COPY --from=build /app/target/*.jar bankapp.jar  

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "bankapp.jar"]
