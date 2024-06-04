FROM  maven:3.9.6-eclipse-temurin-21-alpine AS builder

WORKDIR /

COPY pom.xml .
RUN mvn dependency:resolve
COPY src/ ./src
RUN mvn package

FROM eclipse-temurin:21-jre-alpine
WORKDIR /.
COPY --from=builder /target/worker-jar-with-dependencies.jar .
CMD ["java", "-jar", "worker-jar-with-dependencies.jar"]
