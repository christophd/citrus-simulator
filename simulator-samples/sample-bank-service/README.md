Citrus Bank Service Simulator ![Logo][1]
=============================================
This is a standalone simulator application that simulates a very primitive bank
service. The bank service exposes a REST interface with the following services:
* Calculate-IBAN: a service for calculating the IBAN given a bank account number and sort code
* Validate-IBAN: a service for verifying the IBAN

The simulator has been configured to run using SSL (HTTPS) with a
self-signed certificate on port 8443. You can find the JKS keystore
file containing the certificate under /resources/Keystore/ssl-server.jks.
The properties corresponding to are located in the application.properties file.

In case you wish to regenerate the keystore file you can do this from the
command line using the following command:
```
keytool -genkey -alias selfsigned_localhost_sslserver -keyalg RSA
-keysize 2048 -validity 700 -keypass simulator -storepass simulator
-keystore ssl-server.jks
```

Quick start
---------

You can build the simulator application locally with Maven:

```
mvn clean install
```

This will compile and package all resources for you. Also some prepared Citrus integration tests are executed during the build.
After the successful build you are able to run the simulator with:

```
mvn spring-boot:run
```

Open your browser and point to [https://localhost:8443](https://localhost:8443). You will see the simulator user interface with all available scenarios and
latest activities.

To test the simulator scenarios just use the provided starter-scenarios:
 * TestCalculate
 * TestValidate

You can launch these directly from your browser.

Alternatively just execute the Citrus integration tests which do the same thing as the starters.
Open the Maven project in your favorite IDE and run the tests with TestNG plugins. You should
see the tests calling operations on the simulator in order to receive proper responses. The simulator
user interface should track those interactions accordingly.

Further Information
--------------------

Read the [user manual](https://citrusframework.org/citrus-simulator/) for detailed instructions and features.
For more information on Citrus see [citrusframework.org][2], including a complete [reference manual][3].

 [1]: https://citrusframework.org/img/brand-logo.png "Citrus"
 [2]: https://citrusframework.org
 [3]: https://citrusframework.org/reference/html/
