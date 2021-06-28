#open telemtry - spring boot app maven run

mvn clean install

mvn -pl spboot-tracing-ms1 -am spring-boot:run

mvn -pl spboot-tracing-ms2 -am spring-boot:run

time curl -i localhost:8081/trace/v1/invokeMicroService1


#For Open telemetry steps for jaegar start up 

java -Dotel.exporter=jaeger \
         -Dotel.exporter.jaeger.endpoint=jaeger:14250 \
         -Dotel.exporter.jaeger.service.name=microservice1 \
         -Dapplication.home=/spboot-opentracing/spboot-tracing-ms1/target/ \
         -Dapplication.name=microservice1 \
         -javaagent:/spboot-tracing-ms2/target/opentelemetry-javaagent-all.jar \
         -jar \
         /spboot-tracing-ms2/target/opentracing-ms-2.jar

