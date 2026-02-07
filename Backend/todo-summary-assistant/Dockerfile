#---------Build stage---------#
FROM maven:3.9.6-eclipse-temurin-17 AS build

WORKDIR /todo-summary-assistant

#Copy sourcecode and build the jar
COPY . .
RUN mvn clean install package -DskipTests


# ---------- Runtime stage ----------
FROM eclipse-temurin:17-jre-alpine

WORKDIR /todo-summary-assistant

# Copy only the built JAR from build stage
COPY --from=build /todo-summary-assistant/target/todo-summary-assistant-0.0.1-SNAPSHOT.jar app.jar

# Expose Spring Boot port
EXPOSE 8080

# Run the application
ENTRYPOINT ["java", "-jar", "app.jar"]
