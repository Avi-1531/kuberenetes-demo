#
# Build
#
FROM debian:bullseye AS build

RUN apt-get update && apt-get -y install maven

WORKDIR /opt/shipping

COPY pom.xml /opt/shipping/
RUN mvn dependency:resolve
COPY src /opt/shipping/src/
RUN mvn package

#
# Run
#
# FROM openjdk:8-jdk
# FROM eclipse-temurin:8-jdk
FROM eclipse-temurin:8-jdk-focal

EXPOSE 8080

WORKDIR /opt/shipping

ENV CART_ENDPOINT=cart:8080
ENV DB_HOST=mysql

# mvn package uses pom.xml to:
#     Compile the Java code.
#     Package it into a JAR.
#     By Maven convention, the JAR is placed under target/.
#     The name shipping-1.0.jar comes from the values in pom.xml:
#     xml
    
#     Collapse
#     Copy
#     1
#     2
#     3
#     <groupId>...</groupId>
#     <artifactId>shipping</artifactId>
#     <version>1.0</version>
#     Maven builds: target/<artifactId>-<version>.jar → target/shipping-1.0.jar.
#     So we know /opt/shipping/target/shipping-1.0.jar exists because:
    
#     WORKDIR is /opt/shipping.
#     Maven always writes the packaged artifact under /opt/shipping/target.

COPY --from=build /opt/shipping/target/shipping-1.0.jar shipping.jar

# this -Xmx = max heap
# -Xmn = young gen size
# you can limit so that container does not consume more memory than it should and also it will help in better performance of the application as well because if you give more memory to the application then it will take more time to start and also it will consume more memory and if you give less memory to the application then it will start faster and also it will consume less memory but it may cause
# so we can use 
# CMD ["java","-jar","shipping.jar"]

# It sends an OOM kill (Out Of Memory).
# Result:
# The Java process is killed abruptly.

CMD [ "java", "-Xmn256m", "-Xmx768m", "-jar", "shipping.jar" ]

