# Source - https://stackoverflow.com/q/78455007
# Posted by celikgo
# Retrieved 2026-02-19, License - CC BY-SA 4.0

FROM gradle:8.7-jdk AS build

COPY /src/main ./src/main
COPY /build.gradle ./

COPY build.gradle ./

RUN gradle clean bootBuildImage

FROM eclipse-temurin:21-jre-alpine
WORKDIR /app
COPY --from=build  target/gateway-*.jar app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]
