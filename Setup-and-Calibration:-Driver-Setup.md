# Driver Setup

In OpenPnP, the Driver is the part of the software that interfaces between OpenPnP and a particular type of machine. Typically this is just a small piece of code that translates OpenPnP commands into commands for a particular motion controller such as Smoothie, TinyG, Marlin, etc.

## Choosing a Driver
![screen shot 2016-06-18 at 10 48 23 am](https://cloud.githubusercontent.com/assets/1182323/16172727/d84709b8-3542-11e6-89a3-6890e2f0492e.png)

1. Go to the Machine Setup tab and select the root node of the tree. On most setups it's called "ReferenceMachine". A setup panel will appear on the right.
2. In the setup panel, select the driver that most closely matches you motion controller or machine. Most machines should use the [[GcodeDriver]]. Click apply.
    
    **Note: GcodeDriver is a universal driver that works with many motion controllers. It can be used for TinyG, Smoothie, Marlin, Grbl, etc. You should use GcodeDriver unless you have very specific driver requirements.
3. OpenPnP will prompt you to restart the program, so do that.

## Set Serial Port and Baud rate

Most of the drivers in OpenPnP communicate using the serial port. Before you can connect, you need to set the serial port and baud rate for your controller.

![screen shot 2016-06-18 at 12 28 31 pm](https://user-images.githubusercontent.com/8209285/28393523-d37163d2-6cac-11e7-951b-6a186cd62fa3.png)

1. After restarting OpenPnP go back to the Machine Setup tab and find the Driver you selected in the tree. It should be near the bottom, under the Driver branch. Select it and a setup panel will appear.
2. Select the serial port and baud rate for your controller and press the Apply button.

## Driver Specific Setup

See the pages below for additional information on setting up specific drivers within OpenPnP.

* [[GcodeDriver]]: Recommended for all Gcode based controllers such as Smoothe, Grbl, TinyG, Marlin, etc.

## Connect

Now that the driver is configured, press the green power button <img src="https://rawgit.com/openpnp/openpnp/develop/src/main/resources/icons/power_button_on.svg" height="18"> to connect to your controller. If all goes well the button will turn red and the rest of the controls will become enabled. If there is an issue OpenPnP will give you an error message.

## Homing

If your machine connected successfully it's time to home it. If you don't have home switches installed you can skip this step. To home the machine click the home button ![](https://rawgit.com/openpnp/openpnp/develop/src/main/resources/icons/home.svg).

## Jogging the Machine
![screen shot 2016-06-18 at 10 33 18 am](https://cloud.githubusercontent.com/assets/1182323/16172512/1cf472b0-3540-11e6-987a-fff822524944.png)

With the machine homed, you can now try jogging the machine to make sure everything is working well. Set the Distance slider to 1mm and click the jog buttons ![](https://rawgit.com/openpnp/openpnp/develop/src/main/resources/icons/arrow-left.svg) ![](https://rawgit.com/openpnp/openpnp/develop/src/main/resources/icons/arrow-down.svg) ![](https://rawgit.com/openpnp/openpnp/develop/src/main/resources/icons/arrow-right.svg) ![](https://rawgit.com/openpnp/openpnp/develop/src/main/resources/icons/arrow-up.svg) ![](https://rawgit.com/openpnp/openpnp/develop/src/main/resources/icons/rotate-clockwise.svg) ![](https://rawgit.com/openpnp/openpnp/develop/src/main/resources/icons/rotate-counterclockwise.svg) to move the head around. Make sure that the machine moves in the directions specified by the buttons. If it doesn't, check your controller configuration.

***

| Previous Step                 | Jump To                 | Next Step                                   |
| ----------------------------- | ----------------------- | ------------------------------------------- |
| [[Before You Start|Setup and Calibration: Before You Start]] | [[Table of Contents|Setup and Calibration]] | [[Top Camera Setup|Setup and Calibration: Top Camera Setup]] |