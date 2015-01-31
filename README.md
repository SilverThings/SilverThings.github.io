![Silverspoon.io](images/silverspoon.png)

Java IoT Platform
-----------------

Silverspoon.io aims to provide users with an easy-to-use, though enterprise-ready, IoT platform. Its basic building block is Apache Camel with our custom Camel GPIO Component, allowing users to integrate capabilities of embedded devices with external IT systems, support event-based decision making, or to deploy user applications to IoT gateways as microservices.

Silverspoon IoT Platform is currently under heavy development, however its first (alpha) release of is to come most probably later in 2015, so stay tuned!.

[View on GitHub.](http://github.com/px3/silverspoon)

Camel GPIO Component
--------------------

We have developed a pluggable component for Apache Camel, a light-weight integration framework. This allows us to easily integrate various parts and functionalities of embedded linux platforms using well-known Enterprise Integration Patterns.

```xml
<camelContext trace="false" xmlns="http://camel.apache.org/schema/spring">
  <route customId="true" id="iot-door-route">
	<from uri="gpio://ph7?value=HIGH" />
	<to uri="bean:webCamBean?method=getPicture" />
	<to uri="gpio://pb10?value=HIGH"/>
	<to uri="gpio://pb10?value=LOW"/>
  </route>
</camelContext>
```

[View on GitHub.](http://github.com/px3/camel-gpio)

Bulldog Library
---------------

Bulldog is a Java library providing Java (IoT) developers with GPIO and low-level IO capabilities of embedded linux platforms (BeagleBoneBlack, RaspberryPi, CubieBoard). It's supposed to expose an object-oriented and easy-to-use API offering access to the underlying hardware (GPIOs, I2C, SPI, PWM, etc.).

```java
//Detect the board we are running on
Board board = Platform.createBoard();

//Set up a digital output
DigitalOutput output = board.getPin(RaspiNames.P1_11).as(DigitalOutput.class);

// Blink the LED
output.high();
```

[View on GitHub.](http://github.com/px3/bulldog)
