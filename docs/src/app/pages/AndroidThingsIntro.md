# Android Things

## Introduction

Android Things is a lightweight version of Android that can be flashed onto different hardware prototyping boards, such as Raspberry Pi 3, Intel Edison, Pico or Argon. With Android Things, Google has also provided a library that you can use to build apps that read from and write to different pins on the boards, allowing you to hook up different sensors and actuators. 

The MIT App Inventor Android Things Extension simplifies this further by making the features available in the Android Things SDK even more accessible to developers who might not have previous experience programming IoT devices.

### Supported Hardware Boards

The following are the supported hardware boards as of late August 2017.

- NXP Pico i.MX7D
- NXP Pico i.MX6UL
- NXP Argon i.MX6UL
- NXP SprIoT i.MX6UL
- Raspberry Pi 3

** The MIT App Inventor Components for Android Things **

We have created an extension that is available <a href="http://thilankam.github.io/android-things">here</a>. This extension includes the following four components that can be easily configured in an MIT App Inventor project. The main component necessary is the 'AndroidThingsBoard' component. The devices connected to the board can be modeled using the peripheral components such as 'AndroidThingsGPIO', 'AndroidThingsPWM' and 'AndroidThingsTemperatureSensor'.  

## AndroidThingsBoard

This is a non-visible component that models the Android Things Board. It is responsible for relaying messages between the
IoT devices connected to the board and the MIT App Inventor app.

### Properties

- BoardIdentifier

The string that uniquely identifies the Android Things board that is being configured by the app.

<img src="images/AndroidThingsBoard.Property.BoardIdentifier.png" alt="BoardIdentifier AndroidThingsBoard" width="40%"/>

- HardwarePlatform

The model of the Android Things supported Hardware Platform.

<img alt="HardwarePlatform AndroidThingsBoard" src="images/AndroidThingsBoard.Property.HardwarePlatform.png" width="40%"/>

- MessagingHost

The ipv4 address of the Messaging Server Host.

<img alt="MessagingHost AndroidThingsBoard" src="images/AndroidThingsBoard.Property.MessagingHost.png" width="40%"/>

- MessagingPort

The TCP/IP port that the Messaging Broker is running on.

<img alt="MessagingPort AndroidThingsBoard" src="images/AndroidThingsBoard.Property.MessagingPort.png" width="40%"/>

### Events

- PinConnected

Indicates whether the given pin has connected to a device.

<img alt="PinConnected AndroidThingsBoard" src="images/AndroidThingsBoard.Event.PinConnected.png" width="40%"/>

- PinDisconnected

Indicates whether the given pin has disconnected from the device that was previously attached to.

<img alt="PinDisconnected AndroidThingsBoard" src="images/AndroidThingsBoard.Event.PinDisconnected.png" width="40%"/>

- MessageSent

Indicates that a given message belonging to the given topic is sent through MQTT.

<img alt="MessageSent AndroidThingsBoard" src="images/AndroidThingsBoard.Event.MessageSent.png" width="40%"/>

- MessageReceived

Indicates that a message is received through MQTT.

<img alt="MessageReceived AndroidThingsBoard" src="images/AndroidThingsBoard.Event.MessageReceived.png" width="40%"/>

- HasShutDown

Indicates that the Android Things Board has shutdown.

<img alt="HasShutDown AndroidThingsBoard" src="images/AndroidThingsBoard.Event.HasShutDown.png" width="40%"/>

- ConnectionLost

Indicates that the MQTT connection was lost.

<img alt="ConnectionLost AndroidThingsBoard" src="images/AndroidThingsBoard.Event.ConnectionLost.png" width="40%"/>

### Methods

- Shutdown

Shutdown the Android Things Board.

<img alt="Shutdown AndroidThingsBoard" src="images/AndroidThingsBoard.Method.Shutdown.png" width="40%"/>

- IsShutdown

Determines the status of the AndroidThings Board. Returns true if the Android Things Board has been shutdown.

<img alt="IsShutdown AndroidThingsBoard" src="images/AndroidThingsBoard.Method.IsShutdown.png" width="40%"/>

- IsPinConnected

Returns true if the given pin name is connected to a device.

<img alt="IsPinConnected AndroidThingsBoard" src="images/AndroidThingsBoard.Method.IsPinConnected.png" width="40%"/>

- Initialize

Initializes the AndroidThingsBoard component with the given Hardware Platform, Messaging Host, Port and the identifier given by the companion app running on the AndroidThings device.

<img alt="Initialize AndroidThingsBoard" src="images/AndroidThingsBoard.Method.Initialize.png" width="35%"/>

- HasPin

Checks if the given pin can work on the Android Things Board being used. Returns true if this pin is available on the specified Android Things Board model.

<img alt="HasPin AndroidThingsBoard" src="images/AndroidThingsBoard.Method.HasPin.png" width="35%"/>

- ConnectedPins

Returns the number of connected pins that have active devices attached to.

<img alt="ConnectedPins AndroidThingsBoard" src="images/AndroidThingsBoard.Method.ConnectedPins.png" width="40%"/>

- DisconnectedPins

Returns the number of pins that were registered with the broker, but are now disconnected.

<img alt="DisconnectedPins AndroidThingsBoard" src="images/AndroidThingsBoard.Method.DisconnectedPins.png" width="40%"/>

## AndroidThingsGPIO

This models any device attached to a General Purpose Input and Output (GPIO) pin of a Google Android Things supported hardware platform. This also acts as an MQTT Client, and will either publish or subscribe to certain topic(s). For example, a temperature sensor attached to the board can publish to the topic “temperature”, whereas an LED light can subscribe to the topic “temperature”, and when a certain temperature has exceeded it may be programmed to flash.  The same LED light can subscribe to the topic “message”, and can be programmed to flash in a different sequence when a message is received.

AndroidThingsGPIO component will allow the users to choose the available GPIO pins to make as an input or as an output. The pins can be in either “High” or “Low” state. 
* “High” represents a positive voltage (for Raspberry Pi, it is +3.3 Volts DC). 
* “Low” represents the zero voltage. However, if you do not apply a bias to that pin, the voltage value can float, which means, it can be anywhere between zero and a positive voltage, which can confuse GPIO inputs, Therefore you really need to provide pull-up or pull-down resistance depending on the circuit you are designing.


### Properties

- ConnectedDeviceName

Designates the type of device connected to the pin. For e.g. LED, TemperatureSensor, etc.

<img alt="ConnectedDeviceName AndroidThingsGPIO" src="images/AndroidThingsGPIO.Property.ConnectedDeviceName.png" width="40%"/>

- Message

The message either sent to or received from the endpoint device attached to the pin. For e.g. a TemperatureSensor can publish '80' as the payload.

<img alt="Message AndroidThingsGPIO" src="images/AndroidThingsGPIO.Property.Message.png" width="40%"/>

- PinName

The assigned number for the pin in the Android Things GPIO Header.

<img alt="PinName AndroidThingsGPIO" src="images/AndroidThingsGPIO.Property.PinName.png" width="40%"/>

- PinState

Designates whether the pin is on or off.

<img alt="PinState AndroidThingsGPIO" src="images/AndroidThingsGPIO.Property.PinState.png" width="40%"/>

- Topic

The topic of interest for this pin, in addition to the internally set up topic. For e.g. if the pin is attached to a temperature sensor, this user set topic can be 'temperature'.

<img alt="Topic AndroidThingsGPIO" src="images/AndroidThingsGPIO.Property.Topic.png" width="40%"/>

### Events

- ConnectionLost

Event handler when a message the MQTT connection is lost.

<img alt="ConnectionLost AndroidThingsGPIO" src="images/AndroidThingsGPIO.Event.ConnectionLost.png" width="40%"/>

- MessageReceived

Event handler when a message is received via MQTT.

<img alt="MessageReceived AndroidThingsGPIO" src="images/AndroidThingsGPIO.Event.MessageReceived.png" width="40%"/>

- MessageSent

Event handler when a message is sent through MQTT.

<img alt="MessageSent AndroidThingsGPIO" src="images/AndroidThingsGPIO.Event.MessageSent.png" width="40%"/>

- PinStateChanged

Event handler to return if the state of the pin changed.

<img alt="PinStateChanged AndroidThingsGPIO" src="images/AndroidThingsGPIO.Event.PinStateChanged.png" width="40%"/>

- PinStateChangedToHigh

Event handler to return if the state of the pin changed to HIGH.

<img alt="PinStateChangedToHigh AndroidThingsGPIO" src="images/AndroidThingsGPIO.Event.PinStateChangedToHigh.png" width="40%"/>

- PinStateChangedToLow

Event handler to return if the state of the pin changed to LOW.

<img alt="PinStateChangedToLow AndroidThingsGPIO" src="images/AndroidThingsGPIO.Event.PinStateChangedToLow.png" width="40%"/>

### Methods

- Publish

Publish a message on the subject via the MQTT broker.

<img alt="Publish AndroidThingsGPIO" src="images/AndroidThingsGPIO.Method.Publish.png" width="35%"/>

- Register

Connect to the MQTTBroker, and if the pinDirection is 'in', i.e. a sensor or some other input is connected to the Android Things Board, a message is sent announcing the pin that was registered.

<img alt="Register AndroidThingsGPIO" src="images/AndroidThingsGPIO.Method.Register.png" width="35%"/>

- Subscribe

Subscribes to a topic on the given subject at the given Messaging Host:Port, i.e. MQTT Broker Endpoint.

<img alt="Subscribe AndroidThingsGPIO" src="images/AndroidThingsGPIO.Method.Subscribe.png" width="40%"/>

- Toggle

Changes the state of the pin from HIGH to LOW or vice versa.

<img alt="Toggle AndroidThingsGPIO" src="images/AndroidThingsGPIO.Method.Toggle.png" width="40%"/>

- Unsubscribe

Unsubscribes to a topic on the given subject.

<img alt="Unsubscribe AndroidThingsGPIO" src="images/AndroidThingsGPIO.Method.Unsubscribe.png" width="40%"/>

## AndroidThingsPWM

This models a Pulse Width Modulation (PWM) device attached to an output pin of a Google Android Things supported hardware platform, such as a servo motor or a speaker or an LCD screen display. We can apply a proportional control signal to the external device using a digital output pin. For more information, please see <a href="https://developer.android.com/things/sdk/pio/pwm.html">https://developer.android.com/things/sdk/pio/pwm.html</a>.

### Properties

- DutyCycle

Set the duty cycle. It must be between 1 and 100.

<img alt="DutyCycle AndroidThingsPwm" src="images/AndroidThingsPwm.Property.DutyCycle.png" width="40%"/>

- Enabled

Designates whether the PWM is enabled or not.

<img alt="Enabled AndroidThingsPwm" src="images/AndroidThingsPwm.Property.Enabled.png" width="40%"/>

- Frequency

The frequency of the signal.

<img alt="Frequency AndroidThingsPwm" src="images/AndroidThingsPwm.Property.Frequency.png" width="40%"/>

- PwmName

PWM Pin Identifier.

<img alt="PwmName AndroidThingsPwm" src="images/AndroidThingsPwm.Property.PwmName.png" width="40%"/>

### Methods

- Register

Registers this PWM pin with the AndroidThingsBoard.

<img alt="Register AndroidThingsPwm" src="images/AndroidThingsPwm.Method.Register.png" width="40%"/>

## AndroidThingsTemperatureSensor

This models a non-visible component such as a Temperature Sensor available via the Bmx280SensorDriver that can be attached to a pin of an Android Things supported Hardware Platform.
 
### Properties

- Temperature

Gets the last reported temperature from the Temperature Sensor.

<img alt="Temperature AndroidThingsTemperatureSensor" src="images/AndroidThingsTemperatureSensor.Property.Temperature.png" width="40%"/>

### Events

- TemperatureChanged

Event handler that indicates that the temperature of the sensor has changed or vice versa.

<img alt="TemperatureChanged AndroidThingsTemperatureSensor" src="images/AndroidThingsTemperatureSensor.Event.TemperatureChanged.png" width="40%"/>


### Methods

- Monitor

Monitor the temperature reported by the temperature sensor.

<img alt="Monitor AndroidThingsTemperatureSensor" src="images/AndroidThingsTemperatureSensor.Method.Monitor.png" width="40%"/>

- Register

Registers this temperature sensor with the AndroidThingsBoard.

<img alt="Register AndroidThingsTemperatureSensor" src="images/AndroidThingsTemperatureSensor.Method.Register.png" width="40%"/>


## Setting up your Android Things Board

### Flash the Android Things Image to your board. 

** This is a one time setup **

Depending on the type of board you have, download and install the correct flash image. For example, NXP Pico i.MX7D Flash Image is available <a href="https://developer.android.com/things/hardware/imx7d.html">here</a>, and the Raspberry Pi 3 Flash Image is available <a href="https://developer.android.com/things/hardware/raspberrypi.html">here</a>.

### Install the Android Things App Inventor Companion

You will need to run the Android Things App Inventor Companion available from <a href="https://github.com/thilankam/androidthings-appinventor-companion">https://github.com/thilankam/androidthings-appinventor-companion</a>, in order to send and receive messages to and from your MIT App Inventor that uses the AndroidThings* components.

### Connect your board to WiFi

Make sure your board is connected to WiFi, because otherwise the IoT devices will not be able to communicate with the phone app. If the board is not connected to WiFi, you may run the following command to connect to WiFi:

```javascript 
am startservice -n com.google.wifisetup/.WifiSetupService -a WifiSetupService.Connect -e ssid [your WiFi network] -e passphrase [your WiFi password]
```


### MQTT Broker
[Optional] If you wish to set up your AndroidThings Board as an MQTT broker, we recommend that you install <a href="https://mosquitto.org/">Mosquitto</a>. Follow the instructions given on the Mosquitto website to run a broker locally. Please note that if you wish to control the devices and sensors connected to your Android Things Board via the Internet with this approach, your Board must have a public IP address.
 
Alternatively, you can use one of the public MQTT brokers such as iot.eclipse.org. 
If you wish to secure your payloads, you will need to use SSL ports. Those additional configurations steps are not covered here.

#### Configuration Pairing

When you run the App Inventor Companion on your Android Things board, you should see an information box similar to the following:

```javascript 
*******************************************
Please use the following values when configuring your MIT App Inventor App.
Board Identifier = 269af225-8774-43e1-84d6-b4ebf76ac71e
Hardware Platform Board = iot_imx7d_pico
Messaging Host = iot.eclipse.org
Messaging Port = 1883
*******************************************
```

Make a note of these values as these will be needed when configuring your MIT App Inventor app.


* The "Board Identifier" identifies the Android Things board you are using. This has to match with the identifier used when configuring the App Inventor Board component of your app. Internally, this identifier is used for constructing the MQTT topic, so that only exactly one board will be listening to messages sent to and from your app. This enables us to avoid any potential message collisions when using a public MQTT broker when controlling the devices connected to the Android Things Board via the Internet.  

* The “Hardware Platform” identifies the board type. Based on the value input here, we perform some internal validations on the user input. For example, if the user enters an illegal pin name when configuring an AndroidThings component, an error message is thrown and no MQTT message will be sent. This helps us in avoiding unnecessary delays, and potential erroneous behavior on the Android Things board.

* The 'Messaging Host' and 'Messaging Port' are the settings for the MQTT broker you set up or one of the publicly available brokers.  


# App Inventor Component Configuration 

Before using the AndroidThingsBoard component, we have to initialize the component with certain parameters to make sure the board and the corresponding App Inventor component will work together.

<img alt="Initialize AndroidThingsBoard" src="images/AndroidThingsBoard.Demo.ComponentConfiguration.png" width="40%"/>
 
Similarly, the client components such as the AndroidThingsGPIO, AndroidThingsPwm, and the AndroidThingsTemperatureSensor must be registered. In the tutorials examples how this registration is done is demonstrated.

## Pin Naming

Pin names are very crucial in identifying what devices to control and listen to on your Android Things board. To make the identification as simple as possible, we are adhering to the I/O Pin Outs given in the Official Android Things documentation.

- <a href="https://developer.android.com/things/hardware/imx6ul-pico-io.html">Pico i.MX6UL</a>
- <a href="https://developer.android.com/things/hardware/imx7d-pico-io.html">NXP i.MX7D</a>
- <a href="https://developer.android.com/things/hardware/raspberrypi-io.html">Raspberry Pi 3</a>
- <a href="https://developer.android.com/things/hardware/edison-arduino-io.html">Intel® Edison Arduino</a>
- <a href="https://developer.android.com/things/hardware/edison-sparkfun-io.html">Intel® Edison Sparkfun</a>
- <a href="https://developer.android.com/things/hardware/joule-io.html">Intel® Joule™</a>
