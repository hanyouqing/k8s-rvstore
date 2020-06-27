FROM maven:3.5.2-jdk-8 AS builder
COPY src /usr/src/app/src
COPY pom.xml /usr/src/app
RUN mvn -f /usr/src/app/pom.xml clean package

FROM alpine:latest
COPY --from=builder /usr/src/app/target/order-api-0.0.1-SNAPSHOT.jar /usr/app/order-api-0.0.1-SNAPSHOT.jar

MAINTAINER Tim Solley
USER root

RUN apk update
RUN apk fetch openjdk8
RUN apk add openjdk8

#ADD target/order-api-0.0.1-SNAPSHOT.jar /

ENTRYPOINT java -jar /usr/app/order-api-0.0.1-SNAPSHOT.jar
