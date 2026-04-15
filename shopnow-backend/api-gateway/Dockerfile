# Stage 1: Build the application
FROM eclipse-temurin:17-jdk-jammy AS builder
WORKDIR /app
COPY . .
RUN ./mvnw clean package -DskipTests

# Stage 2: Run the application
FROM eclipse-temurin:17-jre-jammy

WORKDIR /app
COPY --from=builder /app/target/api-gateway-0.0.1-SNAPSHOT.war /app/api-gateway.war

CMD ["java", "-jar", "api-gateway.war"]
