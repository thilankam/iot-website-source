# GPIO Output Demo : Light an LED remotely from your phone! 

This is a basic demo that can be extended to applications for remotely controlling home appliances. For example, a family might go on vacation and forget to turn off the switches in the house, the same family might want to water the plants with their remote controlled plant watering device while they are away. In this example, we will demonstrate how to control a an LED remotely via the Internet.

<iframe width="560" height="315" src="https://www.youtube.com/embed/t-CjMrEeIMM" frameborder="0" allowfullscreen></iframe>

## Functionalities of the App

- LED Switching capability (ON and OFF).


## Prerequisites

Here are the prerequisites for following this tutorial. 
- Knowledge of the App Inventor environment, i.e. how to use the App Inventor Designer View to create the structure of the App
- Importing App Inventor Extensions

## Tutorial Overview

In this tutorial we will use App Inventor to control a simple LED connected to an Android Things board.

### List of Required Equipment 
 
- Android Things Compatible Board such Raspberry Pi 3, NXP Pico i.MX7D, etc.
- 1 LED
- 1 Resistor
- 2 Jumper Wires
- 1 Breadboard

Prepare your Android Things Board as follows:

### Flash the Android Things Image to your board. (** This is a one time setup. **)

Depending on the type of board you have, download and install the correct flash image. For example, NXP Pico i.MX7D Flash Image is available <a href="https://developer.android.com/things/hardware/imx7d.html">here</a>, and the Raspberry Pi 3 Flash Image is available <a href="https://developer.android.com/things/hardware/raspberrypi.html">here</a>.

### Install the Android Things App Inventor Companion

You will need to run the Android Things App Inventor Companion available from <a href="https://github.com/thilankam/androidthings-appinventor-companion">https://github.com/thilankam/androidthings-appinventor-companion</a>, in order to send and receive messages to and from your MIT App Inventor that uses the AndroidThings* components.

### Connect your board to WiFi

Make sure your board is connected to WiFi, because otherwise the IoT devices will not be able to communicate with the phone app. If the board is not connected to WiFi, you may run the following command to connect to WiFi:

```javascript 
am startservice -n com.google.wifisetup/.WifiSetupService -a WifiSetupService.Connect -e ssid [your WiFi network] -e passphrase [your WiFi password]
```

### Create the Circuit

<img alt="AndroidThingsGPIOOutput Circuit" src="images/AndroidThings.Demo.GPIOOutput.Circuit.png"/>

### Run the Android Things App Inventor Companion on your board

You should see something similar to the following on our console. Make a note of these values as these will be needed when configuring your MIT App Inventor app.

```javascript 
*******************************************
Please use the following values when configuring your MIT App Inventor App.
Board Identifier = 269af225-8774-43e1-84d6-b4ebf76ac71e
Hardware Platform Board = iot_imx7d_pico
Messaging Host = iot.eclipse.org
Messaging Port = 1883
*******************************************
```

### Prepare Your App Inventor Instance

Download the Android Things extension from <a href="http://thilankam.github.io/android-things">http://thilankam.github.io/android-things</a>. Upload the extension to your project.

### Create your App Inventor Project

- Create a sample project with On and Off Buttons. We will be using these buttons to control the LED in our circuit.
- Configure the Android Things Components.
    * AndroidThingsBoard#Initialize  method has to be called with the parameters given by your board in a previous step.
        + “identifier”: uniquely matches the messages sent to your board.
        + “hardwarePlatform”: the board type
        + “messagingHost” : the MQTT server address
        + “messagingPort” : the MQTT server port
    * AndroidThingsGPIO#Register method has to be called before any target events or callbacks.
        + “pinName” : the name of the pin as designated in the PinOut diagram for your Android Things compatible board.
        + “isOutput” : the directionality of the pin, i.e. true indicates an output device such as an LED is attached.
        + “androidThingsBoard” : the board that this pin is part of.
- Create the logic for the buttons.
    * “On” Click  Pin state true (turn LED on)
    * “Off” Click  Pin state false (turn LED off)


<img alt="AndroidThingsGPIOOutput App Inventor Design" src="images/AndroidThings.Demo.GPIOOutput.AppInventor.Design.png"/>

<img alt="AndroidThingsGPIOOutput App Inventor Blocks" src="images/AndroidThings.Demo.GPIOOutput.AppInventor.png"/>



