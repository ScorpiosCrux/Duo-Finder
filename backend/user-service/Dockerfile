# Getting maven and packaging application
FROM maven:3.9 AS maven
WORKDIR /duofiner/backend/user-microservice
COPY . /duofiner/backend/user-microservice
RUN mvn package 

# Getting java 17 and executing the application
FROM openjdk:17-oracle
WORKDIR /duofiner/backend/user-microservice
COPY --from=maven /duofiner/backend/user-microservice/target/user-microservice.jar /duofiner/backend/user-microservice
ENTRYPOINT ["sh", "-c", "java -jar ./user-microservice.jar --server.port=${PORT}"]