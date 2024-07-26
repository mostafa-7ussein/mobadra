FROM eclipse-temurin:latest as base

WORKDIR /app

COPY . .

EXPOSE 8080

RUN ./mvnw package
CMD ["/bin/sh", "-c", "java -jar /app/target/*.jar"]
FROM eclipse-temurin:latest AS dev
WORKDIR /app
COPY --from=base /app/target .
ENV STAGE="dev"
EXPOSE 8080
CMD ["/bin/sh", "-c", "java -jar *.jar"]

FROM eclipse-temurin:latest AS prod
WORKDIR /app
COPY --from=base /app/target .
ENV STAGE ="prod"
EXPOSE 8080
CMD ["/bin/sh", "-c", "java -jar *.jar"]