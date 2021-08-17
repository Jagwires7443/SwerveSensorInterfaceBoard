# SwerveSensorInterfaceBoard
Board to Interface an SRX MAG ENCODER to a SPARK MAX and a roboRIO

This small board (2.0" x 0.7") interfaces an SRX MAG ENCODER to a SPARK MAX (A/B incremental encoder inputs plus PWM absolute encoder input, although the latter is not yet supported by SPARK MAX) and to the roboRIO (PWM absolute encoder input used with a digital input; in software used with DutyCycle or DutyCycleEncoder).  The sensor is powered by the motor controller, and the roboRIO is properly isolated.  This is a good starting point for similar interface projects in the FRC (FIRST Robotics Competition) ecosystem.

These are the [KiCad](https://www.kicad.org/) design files, including schematic symbols, PCB footprints, and 3-D models for all the components.

![alt text](https://github.com/Jagwires7443/SwerveSensorInterfaceBoard/blob/main/Board%20Schematic.JPG?raw=true)

![alt text](https://github.com/Jagwires7443/SwerveSensorInterfaceBoard/blob/main/Board%20PCB.JPG?raw=true)

![alt text](https://github.com/Jagwires7443/SwerveSensorInterfaceBoard/blob/main/Board%203D.JPG?raw=true)

Note that a simpler way to handle this is to leave the SPARK MAX out of things and to simply connect pins 2 (+5V), 9 (PWM), and 10 (GND) from the SRX MAG ENCODER to a roboRIO digital input.  Indeed, until REV addresses [this](https://trello.com/c/bvnPPcZD/108-add-continuous-pid-capability) bug, there's not much point in trying to use the SPARK MAX to directly handle closed-loop control.

Working with the 0.05" headers and fine-pitch cables can be tough.  Test that the motor runs as expected before connecting to the SPARK MAX.  Then, be sure the SPARK MAX has been configured to "Alternate Encoder Mode" and this configuration has been saved.  At this point, connect to the SPARK MAX and verify that the LED on the SRX MAG ENCODER is on (any color, the color only depends on the distance to the magnet).  Be sure the LEDs on the SPARK MAX are as expected, and that you can still communicate with it via "REV Hardware Client".  If not, power down and start looking for shorts or opens -- likely trouble spots are the solder connections on the board and the points where the connectors and cables join.  At this point, power and ground are probably good.

Now, check that the motor still runs as expected.  It is possible to short signals which are essential for the motor to run, so suspect a problem in this area if the motor no longer runs well.  Even though these signals normally come in via the built-in signal cable from the (NEO) motor, these same connections are present at the "Data Port".  Trouble in this area may also cause a "Sensor Fault".  If things are all good so far, you can run the motor and should see changing values returned via GetPosition() and GetVelocity().  Finally, check the PWM absolute position signal using a DutyCycle object.  Code to do these things is [here](https://github.com/Jagwires7443/Swerve).  This code contains an extensive test mode (used with Shuffleboard) which will read and display all of the sensor data.

Another option for this type of board is to go surface mount.  The boards REV itself has created seem to use an [FLE-107-01-G-DV](https://www.samtec.com/products/fle-107-01-g-dv-a-tr) connector to directly plug into the SPARK MAX.  Note this is actually a 14-pin connector -- the outer 4 pins are not used to make a connection, but to help to take up some of the excess space on each side of the 10 pins on the connector that is part of the SPARK MAX.  The REV boards are shaped to match the outline of the end of the SPARK MAX where they plug in (roughly 1.13" wide by 0.73" tall, with a roughtly 0.14" by 0.24" notch on each side).
