# Stage 1: Build the JAR
FROM maven:3.8.5-openjdk-11 as builder
WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

# Stage 2: Run the JAR
FROM adoptopenjdk/openjdk11:alpine-jre
WORKDIR /app
COPY --from=builder /app/target/*.jar app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]
