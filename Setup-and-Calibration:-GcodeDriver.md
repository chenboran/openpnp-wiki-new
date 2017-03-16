# GcodeDriver Configuration

GcodeDriver is a universal driver for any controller that uses Gcode. It can even be used with controllers that don't use Gcode, as long as they accept basic text based commands. You should use GcodeDriver unless you have a very unique machine that requires a special, custom driver.

This page is intended to guide the reader through a basic GcodeDriver setup. For more advanced information, see [[the complete GcodeDriver reference|GcodeDriver]].

## Preparation

Before starting to configure the driver you should collect some information about your machine:
1. What kind of controller are you using? Some common ones are SmoothieBoard, Cohesion3D ReMix (Smoothie), Grbl, Marlin and TinyG.
2. Find the command reference for your controller:
    * Smoothie: http://smoothieware.org/supported-g-codes
    * Grbl: https://github.com/gnea/grbl/blob/master/doc/markdown/commands.md
    * Marlin: http://marlinfw.org/meta/gcode/
    * TinyG: https://github.com/synthetos/TinyG/wiki/Gcode-Support
3. Make sure you've selected the GcodeDriver in OpenPnP and restarted it. If you haven't done that yet, see https://github.com/openpnp/openpnp/wiki/Setup-and-Calibration%3A-Driver-Setup.

## Document The Hardware

Next you'll document all the hardware in the machine. This will help you determine what commands you need to configure the driver with.

1. Make a list of each device on the machine you want to control from OpenPnP. This should include motors, pumps, solenoid valves, feeders, cameras, camera lighting, etc.
    
    As an example, my machine hardware list looks like this: X stepper, Y stepper, Z stepper, nozzle 1 rotation stepper, nozzle 2 rotation stepper, top camera, bottom camera, camera LEDs, vacuum pump, nozzle 1 vacuum solenoid, nozzle 1 exhaust solenoid, nozzle 2 vacuum solenoid, nozzle 2 exhaust solenoid.
2. Now go back to the list and write down the commands needed to control each device. These will typically be Gcode G or M commands.

    Use the reference you found above, along with a tool like [Printrun](https://github.com/kliment/Printrun) to make sure you can control every device.

    If your controller requires commands for startup, homing, enable, disable, etc. you should add those items to the list too.

    Your list should now look something like this:
    * Connect: G21, G90, M82
    * Enable: M801, M803, M805, M807, M809, M810
    * Disable: M801, M803, M805, M807, M809, M811
    * Home: M84, G92 Z0, G28 X0 Y0, T1, G92 E0, T0 G92 E0
    * X stepper: G0 Xnnn
    * Y stepper G0 Ynnn
    * Z stepper G0 Znnn
    * nozzle 1 rotation stepper: T0 G0 Ennn
    * nozzle 2 rotation stepper: T1 G0 Ennn
    * top camera: USB
    * bottom camera: USB
    * camera LEDs: M810 on, M811 off
    * vacuum pump: M808 on, M809 off
    * nozzle 1 vacuum solenoid: M800 on, M801 off
    * nozzle 1 exhaust solenoid: M802 on, M803 off
    * nozzle 2 vacuum solenoid: M804 on, M805 off
    * nozzle 2 exhaust solenoid M806 on, M807 off

## Multiple Controllers

The GcodeDriver supports controlling multiple controllers at once. This uses a concept called sub-drivers that will be explained below. For now, just remember that if you have multiple controllers you'll need to know which one controls each device too.

## Configure Primary Controller

Your primary controller is typically the one that controls X and Y. If you don't have multiple controllers then this is the only one you'll need to configure.

### Serial Port
1. Open the GcodeDriver settings by going to Machine Setup -> Driver -> GcodeDriver and selecting it. The GcodeDriver configuration panel will open below.
2. In the settings below, open the Serial tab.
3. Select the port for your controller from the dropdown.
4. Select the baud rate.
5. Select any other less common settings that your serial port requires.
6. Click Apply.

### General Settings
1. Select the General Settings tab.
2. Set the Units that your controller uses for movement.
3. Set the max feed rate in Units per Minute. This should match the maximum setting in your controller.
4. If your controller requires a long time to respond after being opened, increase the Connect Wait Timeout.
5. If you have commands that take a very long time to run, increase the Command Timeout.

### Gcode
The Gcode tab is where the vast majority of the work will be done. This is where you will add all the commands you listed above.

