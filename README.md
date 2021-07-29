# SwerveSensorInterfaceBoard
Board to Interface an SRX MAG ENCODER to a SPARK MAX and a roboRIO

This small board (2.0" x 0.7") interfaces an SRX MAG ENCODER to a SPARK MAX (A/B incremental encoder inputs plus PWM absolute encoder input, although the latter is not yet supported by SPARK MAX) and to the roboRIO (PWM absolute encoder input used with a digital input; in software used with DutyCycle or DutyCycleEncoder).  The sensor is powered by the motor controller, and the roboRIO is properly isolated.  This is a good starting point for similar interface projects in the FRC (FIRST Robotics Competition) ecosystem.

These are the [KiCad](https://www.kicad.org/) design files, including schematic symbols, PCB footprints, and 3-D models for all the components.

![alt text](https://github.com/Jagwires7443/SwerveSensorInterfaceBoard/blob/main/Board%20Schematic.JPG?raw=true)

![alt text](https://github.com/Jagwires7443/SwerveSensorInterfaceBoard/blob/main/Board%20PCB.JPG?raw=true)

![alt text](https://github.com/Jagwires7443/SwerveSensorInterfaceBoard/blob/main/Board%203D.JPG?raw=true)
