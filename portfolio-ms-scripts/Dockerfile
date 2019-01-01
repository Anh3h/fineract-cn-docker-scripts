FROM openjdk:8-jdk-alpine

ARG portfolio_port=2025

ENV server.max-http-header-size=16384 \
    bonecp.partitionCount=1 \
    bonecp.maxConnectionsPerPartition=4 \
    bonecp.minConnectionsPerPartition=1 \
    bonecp.acquireIncrement=1 \
    server.port=9090 \
    cassandra.clusterName="Test Cluster" \
    cassandra.contactPoints=cassandra.service:9042 \
    cassandra.keyspace=seshat \
    cassandra.cl.read=ONE \
    cassandra.cl.write=ONE \
    cassandra.cl.delete=ONE \
    mariadb.driverClass=org.mariadb.jdbc.Driver \
    mariadb.database=seshat \
    mariadb.host=mariadb.service \
    mariadb.port=3306 \
    mariadb.user=root \
    mariadb.password=mysql \
    spring.cloud.discovery.enabled=false \
    spring.cloud.config.enabled=false \
    flyway.enabled=false \
    feign.hystrix.enabled=false \
    ribbon.eureka.enabled=false \
    ribbon.listOfServers=eureka.service:9090 \
    eureka.client.serviceUrl.defaultZone=http://eureka.service:8761/eureka \
    spring.cloud.discovery.enabled=true \
    eureka.instance.hostname=eureka.service \
    eureka.client.fetchRegistry=true \
    eureka.registration.enabled=false \
    eureka.instance.leaseRenewalIntervalInSeconds=1 \
    eureka.client.instanceInfoReplicationIntervalSeconds=1 \
    activemq.brokerUrl=tcp://activemq.service:61616 \
    ribbon.eureka.enabled=true \
    portfolio.bookLateFeesAndInterestAsUser=imhotep \
    system.initialclientid=service-runner

WORKDIR /tmp
COPY portfolio-service-boot-0.1.0-BUILD-SNAPSHOT.jar .
ENV spring.application.name="portfolio-v1" \
    server.port=$portfolio_port \
    server.contextPath="/portfolio-v1"

CMD ["java", "-jar", "portfolio-service-boot-0.1.0-BUILD-SNAPSHOT.jar"]
