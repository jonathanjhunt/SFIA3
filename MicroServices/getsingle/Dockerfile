FROM maven:latest AS build-stage
COPY . ./build
WORKDIR ./build
EXPOSE 8081
RUN mvn clean package
 
FROM java:8 AS runtime
WORKDIR /opt/fit
COPY --from=build-stage /build/target/*.jar app.jar
EXPOSE 8081
ENTRYPOINT ["/usr/bin/java", "-jar", "app.jar"]
