# Dual motor control by L298N motor driver

If we directly connect motor with ardrino it will only get **5V** and **20mA** current, which is not enough voltage and current. Therefore, we use L298N motor driver to control DC motors. 
> ## What is L298N motor driver?
L298N motor driver is also known as H-bridge motor driver. It is a useful device that helps control the speed and direction of two DC motors or one stepper motor.  
 It's popular in robot and automation projects because it can handle high currents and works well with common microcontrollers like Arduino and Raspberry Pi. 
#### Pins in L298N driver:   
The board has four input terminals plus two enable terminals. You will use these terminals to control both direction and speed or each motor. They are as follows:  
- IN1 – Input 1 for Motor A  
- IN2 – Input 2 for Motor A  
- IN3 – Input 3 for Motor B  
- IN4 – Input 4 for Motor B 
- EN1 – Enable line for Motor A  
- EN2 – Enable Line for Motor B     
- pin1,pin2 - for controlling Motor A     
- pin3,pin4 - for controlling Motor B

## Supplies
Following are the components needed:  
1) Arduino Uno 
2) Dual H-Bridge   
3) Motor Driver 
4) 12v power supply  
5) Jumper wires

> ## how to wire an H-bridge motor driver with DC motors?

By following below steps DC motors can be connect through H-bridge:  
### Step1: Wire DC motos to H-bridge
Connect motor A into pin1,pin2 and motor B into pin3,pin4 in the H-Bridge, as shown below.  

![H brige](/Images//L298nS1.PNG)  

### Step2: Connect Control Pins Into Arduino  
 *(here arduino UNO is used)*.  
 Connect motor A control pins IN1,IN2 into digital (i-e pin5,pin4)and motor B control pins IN3,IN4 into digital (i-e pin3,pin2) in the Arduino board.

![H brige](/Images//L298mS2.PNG)  
> NOTE : remember to connect control pins into the output pins which can do pulse width modulation (PWM) marked with ~ (tilde mark)

### Step3: Connecting to the Power Supply.  
 Connect the +12V pin of the H-Bridge to the +Vcc of the power source. Connect the GND pin of the H-Bridge to the GND of the Arduino Uno board.
Power the Arduino Uno board by connecting the +5V pin of the H-Bridge to the Vin pin of the Arduino Uno board.

![H brige](/Images//L298nS3.PNG) 

### Step 4: Arduino Sketch

```c++
// Define motor control pins
 int motorA_IN1 = 5;  // Motor A control pin 1
 int motorA_IN2 = 4;  // Motor A control pin 2
 int motorB_IN3 = 3;  // Motor B control pin 1
 int motorB_IN4 = 2;  // Motor B control pin 2

void setup() {
  // Set motor control pins as outputs
  pinMode(motorA_IN1, OUTPUT);
  pinMode(motorA_IN2, OUTPUT);
  pinMode(motorB_IN3, OUTPUT);
  pinMode(motorB_IN4, OUTPUT);
}

void loop() {
  // Example: Move Motor A forward
  digitalWrite(motorA_IN1, HIGH);
  digitalWrite(motorA_IN2, LOW);

  // Example: Move Motor B forward
  digitalWrite(motorB_IN3, HIGH);
  digitalWrite(motorB_IN4, LOW);

  delay(1000);  // Run motors for 1 second

  // Example: Move Motor A backward
  digitalWrite(motorA_IN1, LOW);
  digitalWrite(motorA_IN2, HIGH);

  // Example: Move Motor B backward
  digitalWrite(motorB_IN3, LOW);
  digitalWrite(motorB_IN4, HIGH);

  delay(1000);  // Run motors for 1 second

  // Example: Stop both motors
  digitalWrite(motorA_IN1, LOW);
  digitalWrite(motorA_IN2, LOW);
  digitalWrite(motorB_IN3, LOW);
  digitalWrite(motorB_IN4, LOW);

  delay(1000);  // Stop motors for 1 second
}
```
This code sets up the motor control pins as outputs and then moves each motor forward and backward with a delay in between. You can adjust the digitalWrite and delay values to control the speed and direction of the motors according to your requirements.
