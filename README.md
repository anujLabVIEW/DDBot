# Differential Drive Robot

#### Abstract
This library allows you to control a differential drive robot using L293D, L298 or similar motor drivers. It mainly condenses long confusing functions into simple single-line ones. Although it is designed specifically for the Level 3 course offered to schools in Bangalore by [Just Robotics](https://www.justrobotics.in/), it can be used for robots that follow a similar configuration.
## Robot configuration
A motor driver IC such as L293D connects to two motors (you can use four or more as well but they will not get individual control - at least not yet - and you must connect them all in parallel to the same L293D port). One motor port drives the wheel(s) on the left side; the other is responsible for the right side.
## Purpose of DDBot
Typically, such motors are controlled using four DIO pins on the Arduino board and can result in large and confusing chunks of code just to write to DIO pins. For example, you will need all the four lines below just to move forward.

      digitalWrite(pin1, HIGH);
      digitalWrite(pin2, LOW);
      digitalWrite(pin3, HIGH);
      digitalWrite(pin4, LOW);

This library works by condensing much of this code down to single-line functions.

      motors.forward();

Using the PWM pins on the board, many motor drivers allow you to control the speed of the motors. This library also simplifies that by requiring you to enter values as percentage (0 to 100) rather than the default 0 to 255.
## What can you do with it?
### Command directions
The library has nine functions for specifying the direction the robot can move in, including one to stop.

      forward()             // Move the robot forward
      backward()            // Move the robot backward
      clockwise()           // Make the robot rotate clockwise
      counterClockwise()    // Make the robot rotate counter-clockwise
      leftF()               // Move the robot forward, curving left
      leftB()               // Move the robot backward, curving left
      rightF()              // Move the robot forward, curving right
      rightB()              // Move the robot backward, curving right
      stop()                // Stop the robot

If you so prefer, a function also allows you to enter simple Boolean values for writing to the motors.

      custom(1, 0, 1, 0)    // Move the robot forward

### Control speed
The library allows you to set the speed of the robot, either using a single PWM pin common to both motors, or using one for each. The functions let you set the speed either explicitly, or as argument(s) in command directions.
