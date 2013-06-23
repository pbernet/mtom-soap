An example project that demonstrates sending large files via SOAP with attachment streaming on both client and server.

### Structure

`mtom-soap-client` — the client based on Apache CXF

`mtom-soap-common` — WSDL schema of the service, build-time generated JAXB2 and CXF classes

`mtom-soap-server` — the server application based on Spring Web Services and SAAJ

### Software

* Oracle JDK 1.7.0_25
* Apache Tomcat 7.0.41

### Configuration

`mtom-soap-server/src/main/resources/settings.properties` — the `upload.path` property sets the directory for the server to upload files to. It refers to the Apache Tomcat temp folder by default.

`mtom-soap-common/src/main/resources/service.wsdl` — the port binding refers to URL http://localhost:8080/server/ which is the expected URL of the server application.

### Running the example

1. Run mvn clean package. The CXF and JAXB2 classes will be generated.
2. Deploy the mtom-soap-server service on Apache Tomcat.
3. Start Apache Tomcat with JVM argument `-Dsaaj.use.mimepull=true` — this enables attachment streaming for Sun's implementation of SAAJ bundled with Oracle JDK.
4. Run the SampleClient class from mtom-soap-client. It takes the name of the file to attach as an argument.

