# ----------- Stage 1: Build -----------
FROM maven:3.9.9-eclipse-temurin-21 AS builder

WORKDIR /app
COPY . .

# Build file .jar
RUN mvn clean package -DskipTests


# ----------- Stage 2: Run -------------
FROM eclipse-temurin:21-jdk

WORKDIR /app

COPY --from=builder /app/target/*.jar app.jar

# Render sẽ inject biến môi trường PORT (vd: 10000)
EXPOSE ${PORT}

# Bắt Spring Boot chạy đúng port Render cung cấp
ENTRYPOINT ["java", "-jar", "app.jar"]
