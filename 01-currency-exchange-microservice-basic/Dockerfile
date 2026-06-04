# FROM maven:3.8.2-jdk-8-slim AS build
# WORKDIR /home/app
# COPY . /home/app
# RUN mvn -f /home/app/pom.xml clean package

# FROM openjdk:8-jdk-alpine
# VOLUME /tmp
# EXPOSE 8000
# COPY --from=build /home/app/target/*.jar app.jar
# ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -Djava.security.egd=file:/dev/./urandom -jar /app.jar" ]



FROM maven:3.9.6-eclipse-temurin-17 AS build

WORKDIR /home/app

COPY . .

RUN mvn clean package

FROM eclipse-temurin:17-jre

WORKDIR /

COPY --from=build /home/app/target/*.jar app.jar

EXPOSE 8000

ENTRYPOINT ["java","-jar","app.jar"]