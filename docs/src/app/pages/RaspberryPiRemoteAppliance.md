# Remote Controlled Home Appliances 

There are many applications for remotely controlling home appliances. For example, a family might go on vacation and forget to turn off the switches in the house, the same family might want to water the plants with their remote controlled plant watering device while they are away. In this example, we will demonstrate how to control a home appliance remotely via the Internet.

## Functionalities of the App

- Device Switching capability (ON and OFF).
- (Optional ) Switch a device connected to a Raspberry Pi ON or OFF according to a schedule (i.e  water the plants at 7:00pm).

## Prerequisites

Here are the prerequisites for following this tutorial. 
- Knowledge of the App Inventor environment, i.e. how to use the App Inventor Designer View to create the structure of the App.
- Use of sensors and how to connect the sensors to the Raspberry Pi device.
- Raspberry Pi AppInventor Companion running on the RaspberryPi device as explained in the 
<a rel="nofollow" href="https://docs.google.com/document/d/1AzBV36rJg7dyHWAOJNvxOadOa7NXaQPUpm_9Zn_rhWw/edit#">here.</a>  Setting up RaspberryPi section.

## Tutorial Overview

This tutorial is segmented into two parts that the second part is an advancement of the functionality of the first one.
 
* Part 1 : Beginner Level
& Part 2 : Advanced/Intermediate Level.
 
Part 1 contains a low voltage LED light as the security light and the Part 2 contains the advancemed version that uses domestic light as the security light with 120 V higher voltage. 

***
WARNING : DANGER 
***
Part 2 is NOT for the children and minors. Also Part 2 is NOT for the adults that are not familiar with proper and safely  working with domestic high voltage electricity.  Part 2 is only for the adult professionals who knows how to work safely with domestic electricity. 
***

## Part 1 : Beginner Level

In this tutorial we will use App Inventor to control a simple LED connected to the RaspberryPi.

### List of Required Equipment 
 
1. Raspberry Pi 2B or 3 board
2. Breadboard 
3. Jumpers (male-to-male and male-to-female)
4. Resistors
5. [Optional] GPIO to Breadboard Interface Board (40 Pin T-Shaped) 
6. [Optional] GPIO Ribbon Cable 

### Circuit Diagram

<div style="text-align: center; font-size: 75%; margin: 16pt 0;">
![raspberry:pi Conceptual Circuit Diagram](./images/RaspberryPi.PhysicalCircuitDiagram.png)
![raspberry:pi Physical Circuit Diagram](./images/RaspberryPi.LogicalCircuitDiagram.png)
<br>
Conceptual and Physical Circuit Diagrams
</div>

### App Inventor Design

![intializeServer_registerPin RaspberryPiServer1](images/RaspberryPi.RemoteAppliance.png)

### Resource Download

The <a rel="nofollow" href="https://drive.google.com/open?id=0B-k0lzwhCAU8anQxWFN2d1M2U1k">aia</a> and the <a rel="nofollow" href="https://drive.google.com/open?id=0B-k0lzwhCAU8X1hwaUsyRTE1ejg">apk</a> content of this example can be downloaded here if you are planning not to create the App it by yourself (but we recommend you to build your own app using MIT App Inventor by following this tutorial).

## Part 2 : Advanced/Intermediate Level

Next, instead of the LED attached to a breadboard, we’ll see how we can modify the circuit above to control household appliances such as table lamps, etc.

### List of Required Equipment 

1. Raspberry Pi 2B or 3 board
2. Breadboard 
3. Jumpers (male-to-male and male-to-female)
4. Pushbutton 
5. Resistors
6. Table Lamp
7. Surge Protector 
8. Power supply

### Circuit Setup

![remoteAppliancePart2 RaspberryPiServer1](images/RaspberryPi.RemoteAppliancePart2.png)

### App Inventor Design

The app inventor design is the same as in the Part 1: Beginner Level of this tutorial.

### Demo Video

<a href="http://www.youtube.com/watch?feature=player_embedded&v=HecuphkD3ic
" target="_blank"><img src="http://img.youtube.com/vi/HecuphkD3ic/0.jpg" 
alt="Raspberry Pi and MIT App Inventor (Raspberry Pi GPIO pin control using MIT App Inventor ) " width="240" height="180" border="10" /></a>




