# Servo motor

A servo motor is a distinct type of electric motor engineered for accurate control of angular or linear position, velocity, and acceleration. Unlike conventional motors that rotate continuously, servo motors are designed to move to a specific position and maintain that position based on an external control signal. This feature makes them essential in applications that demand precise positioning and controlled movement.

![servo](/Images/Servo%20Motor.jpg)

Here is a overwiew of topic of discussion:
- [Components insight servo motor](#key-components-of-a-servo-motor)
- [working principle of servo](#working-principle)
- [Components needed for wiring](#components)
- [Wiring](#connection)
- [Arduino code](#arduino-sketch)
- [<servo.h> header file usage](#servoh-header-file-overview)


## Key Components of a Servo Motor

- **Motor:** Typically a DC motor, though AC motors can also be used. It provides the necessary movement.
- **Control Circuit:** Manages the input signals and controls the motor’s motion.
- **Position Sensor:** Often a potentiometer or encoder, it provides feedback on the motor’s position, enabling precise control.  
- **Gearbox:** Reduces the motor’s speed while increasing torque, enabling the motor to perform tasks that require greater force with enhanced precision.

![inner view](/Images/servo%20inner%20view.png)

## Working Principle

Servo motors work using a system called closed-loop control, which means they continuously check and adjust their movement to ensure they are in the right position. Here's how it works in simple terms:

- **Receive a Control Signal:** The motor gets a signal that tells it what position to move to. This signal is usually in the form of Pulse Width Modulation (PWM).
- **Compare Positions:** The motor uses a sensor to check its current position and compares it to the desired position.
- **Adjust Movement:** If the current position is different from the desired position, the motor changes its movement to correct the difference, making sure it reaches and holds the exact position needed.

> *Usually, they have a servo arm that can turn 180 degrees. Using the Arduino, we can tell a servo to go to a specified position and it will go there. As simple as that*

## Components 

Following things are needed:

1) An Arduino board connected to a computer via USB
2) A servo motor
3) Jumper wires

## Connection

Here we will see how to connect a servo motor and then how to turn it to different positions:  
- Connect the `VCC` servo motor wire to the `5V` pin of Arduino.
- Attach the `GND`  servo motor wire to any `GND` pin of Arduino.
- Link the `Signal` servo motor wire to a digital pin( PWM-capable) on the Arduino, such as `pin 9`.

![connection](/Images/servo%20connection.PNG)

## Arduino sketch

```C++

#include <Servo.h>

Servo myservo;  // Create a servo object

void setup() {
  myservo.attach(9);  // Attach the servo to pin 9
}

void loop() {
  myservo.write(0);   // Move servo to 0 degrees
  delay(1000);        // Wait for 1 second
  myservo.write(90);  // Move servo to 90 degrees
  delay(1000);        // Wait for 1 second
  myservo.write(180); // Move servo to 180 degrees
  delay(1000);        // Wait for 1 second
}

```

## <servo.h> header file overview

- *Usage:* The Servo.h header file in Arduino is a library that provides a simple way to control servo motors.  
- *Purpose:* The Servo.h library allows you to easily control servo motors by generating PWM (Pulse Width Modulation) signals that dictate the servo's position.
- *Servos Supported:* The library supports both standard and continuous rotation servos.
### Usage 

1) **Including the Library** 
First, include the library at the beginning of your sketch:

```C++
#include <Servo.h>
```
2) **Creating a Servo Object**
Create an instance of the Servo class:
```C++
Servo myServo;
```
3) **Attaching the Servo**
Attach the servo to a specific PWM pin:
```C++
myServo.attach(9); // Attach the servo to pin 9
```
4) **Writing Positions**
To set the position of the servo (0 to 180 degrees):
```C++
myServo.write(90); // Set servo to 90 degrees
```
5) **Detaching the Servo**
To detach the servo, which stops the PWM signal:
```C++
myServo.detach();
```
