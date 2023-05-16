# Getting maven and packaging application
FROM maven:3.9 AS maven
WORKDIR /duofiner/backend/chat-microservice
COPY . /duofiner/backend/chat-microservice
RUN mvn package 

# Getting java 17 and executing the application
FROM openjdk:17-oracle
WORKDIR /duofiner/backend/chat-microservice
COPY --from=maven /duofiner/backend/chat-microservice/target/chat-microservice.jar /duofiner/backend/chat-microservice
ENTRYPOINT ["sh", "-c", "java -jar ./chat-microservice.jar --server.port=${PORT}"]