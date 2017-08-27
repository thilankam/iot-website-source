# PWM Demo: Create a mini water sprinkler system using a small servo! 

In this tutorial we will see how we can change the PWM values programmatically to create a mini water sprinkler.

<iframe width="560" height="315" src="https://www.youtube.com/embed/5WToT21FYy0" frameborder="0" allowfullscreen></iframe>

## Functionalities of the App

- Make a servo move to simulate a mini water sprinkler system

## Prerequisites

Here are the prerequisites for following this tutorial. 
- Knowledge of the App Inventor environment, i.e. how to use the App Inventor Designer View to create the structure of the App
- Importing App Inventor Extensions
- Basic Looping
- Variable Manipulation

## Tutorial Overview

In this tutorial we will use App Inventor to control a servo connected to an Android Things board.

### List of Required Equipment 
 
- Android Things Compatible Board such Raspberry Pi 3, NXP Pico i.MX7D, etc.
- 1 Servo
- 3 Jumper Wires
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

<img alt="AndroidThingsPWM Circuit" src="images/AndroidThings.Demo.PWM.Circuit.png"/>

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

- Create a sample project with a buttons and a label. 
    * "Run Sprinkler" button: To change the DutyCycle of the AndroidThingsPWM Component.
        + This specific program changes the DutyCycle value in a loop to emulate a 'sprinkler' system.
        + Changes in the sprinkler's direction is also calculated.
    * AndroidThingsPWM: Component that models an Android Things PWM device.
    * Clock - To use in the delay procedure.
- Configure the Android Things Components.
    * AndroidThingsBoard#Initialize  method has to be called with the parameters given by your board in a previous step.
        + "identifier": uniquely matches the messages sent to your board.
        + "hardwarePlatform": the board type
        + "messagingHost" : the MQTT server address
        + "messagingPort" : the MQTT server port
    * AndroidThingsPwm#Register method has to be called before any target events or callbacks.
        + "Register"  method has to be called before any target events or callbacks.
        + "pwmName" : the name of the pin as designated as the PWM port in the PinOut diagram for your Android Things compatible board.
        + "androidThingsBoard" : the board that this pin is part of.
- Create the logic for the app.
    * Initialize Global Variables.
    * Create the Delay Procedure. This procedure 'sleeps' for a small predetermined period of time.
    * Button Click
        + Run the stepper motor like a mini water sprinkler.
        + The direction of the motor and the duty cycle are changed in a loop.
        + The delay procedure is called in each iteration of the loop.


<img alt="AndroidThingsPwm App Inventor Design" src="images/AndroidThings.Demo.Pwm.AppInventor.Design.png"/>

<img alt="AndroidThingsPwm App Inventor Blocks" src="images/AndroidThings.Demo.Pwm.AppInventor.Blocks.png"/>
