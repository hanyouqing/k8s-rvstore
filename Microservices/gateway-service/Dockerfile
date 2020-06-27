FROM maven:3.5.2-jdk-8 AS builder
COPY src /usr/src/app/src
COPY pom.xml /usr/src/app
RUN mvn -f /usr/src/app/pom.xml clean package

FROM alpine:latest
COPY --from=builder /usr/src/app/target/gateway-service.jar /usr/app/gateway-service.jar

MAINTAINER Tim Solley
USER root

RUN apk update
RUN apk fetch openjdk8
RUN apk add openjdk8

ENTRYPOINT java -jar /usr/app/gateway-service.jar