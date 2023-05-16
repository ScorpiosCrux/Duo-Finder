# Getting maven and packaging application
FROM maven:3.9 AS maven
WORKDIR /duofiner/backend/matching-microservice
COPY . /duofiner/backend/matching-microservice
RUN mvn package 

# Getting java 17 and executing the application
FROM openjdk:17-oracle
WORKDIR /duofiner/backend/matching-microservice
COPY --from=maven /duofiner/backend/matching-microservice/target/matching-microservice.jar /duofiner/backend/matching-microservice
ENTRYPOINT ["sh", "-c", "java -jar ./matching-microservice.jar --server.port=${PORT}"]