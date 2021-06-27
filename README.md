open telemtry - spring boot app maven run
mvn clean install
mvn -pl spboot-tracing-ms1 -am spring-boot:run
mvn -pl spboot-tracing-ms2 -am spring-boot:run
time curl -i localhost:8081/trace/v1/invokeMicroService1

##
For Open telemetry steps for running as docker
