# Getting maven and packaging application
FROM maven:3.9 AS maven
WORKDIR /duofiner/backend/gateway-microservice
COPY . /duofiner/backend/gateway-microservice
RUN mvn package 

# Getting java 17 and executing the application
FROM openjdk:17-oracle
WORKDIR /duofiner/backend/gateway-microservice
COPY --from=maven /duofiner/backend/gateway-microservice/target/gateway-microservice.jar /duofiner/backend/gateway-microservice
ENTRYPOINT ["sh", "-c", "java -jar ./gateway-microservice.jar --server.port=${PORT}"]