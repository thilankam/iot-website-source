#  Temperature Sensor Demo: Monitor the temperature of a room remotely from your phone! 

Monitoring the temperature of a room remotely has many advantages. It can help us detect any potential fires and take necessary action such as sound an alarm or notify the fire department. Similarly, we can monitor the temperature of the home, and turn on and off the air-conditioning or the heater as needed, remotely, only when required. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/IJiL7BhVE-Y" frameborder="0" allowfullscreen></iframe>

## Functionalities of the App

- Monitor the temperature
- Change the background of the app based on temperature thresholds for hot and cold

## Prerequisites

Here are the prerequisites for following this tutorial. 
- Knowledge of the App Inventor environment, i.e. how to use the App Inventor Designer View to create the structure of the App
- Importing App Inventor Extensions
- Variable Manipulation

## Tutorial Overview

In this tutorial we will use App Inventor to monitor a temperature sensor connected to an Android Things board.

### List of Required Equipment 
 
- Android Things Compatible Board such Raspberry Pi 3, NXP Pico i.MX7D, etc.
- Pimoroni Rainbow HAT for Android Things (Rainbow HAT has a built-in temperature sensor)

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

<img alt="AndroidThingsTemperatureSensor Circuit" src="images/AndroidThings.Demo.TemperatureSensor.Circuit.png"/>

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

- Create a sample project with Labels, Text Boxes and a Button.
	* We will be using two Text Boxes to get input values for temperature thresholds and a button to start monitoring current temperature. 
 - Configure the Android Things Components.
    * AndroidThingsBoard#Initialize  method has to be called with the parameters given by your board in a previous step.
        + "identifier": uniquely matches the messages sent to your board.
        + "hardwarePlatform": the board type
        + "messagingHost" : the MQTT server address
        + "messagingPort" : the MQTT server port
    * AndroidThingsTemperatureSensor#Register method has to be called before any target events or callbacks.
        + "androidThingsBoard" : the board that this pin is part of.
- Create the logic for the app.
    * "Monitor Temperature" Button Click:
    	+ Start monitoring the current temperature.
    * Text Boxes:
    	+ Hot Threshold Text Box will intake the input value from user.
		+ Cold Threshold Text Box will intake the input value from user.
    * AndroidThingsTemperatureSensor#TemperatureChanged Event:
        + Compare the reported temperature with the hot and cold temperature thresholds input by the user.
        + If the temperature is less than the cold threshold turn background color to blue.
		+ If the temperature is more than the hot threshold turn background color to red.
		+ If the temperature is in between the hot and cold thresholds turn background color to green.
        
<img alt="AndroidThingsTemperatureSensor App Inventor Design" src="images/AndroidThings.Demo.TemperatureSensor.AppInventor.Design.png"/>

<img alt="AndroidThingsTemperatureSensor App Inventor Blocks" src="images/AndroidThings.Demo.TemperatureSensor.AppInventor.Blocks.png"/>


