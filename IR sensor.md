# IR sensor 

Infrared Sensor is used as a motion control for arduino. It measures Infrared radiations from it's surroundings and give an electronic signal as an output. 

## Types of IR sensor

The types of IR sensor are:
1) Active IR sensor
2) Passive IR sensor

### Active IR sensor
Actice IR sensor emmits and detect infrated radiations, it is made up of two parts: 
- **light emmitinf diode** : tramsmits Infrared radiations 
- **Photodiode** : recives Infrared radiations 

![AIR](/Overview%20of%20the%20Arduino%20Components.md/AIR.PNG)

When an object approaches the sensor, the infrared light from the LED bounces off the item and is recognized by the receiver.

Active IR sensors act as proximity sensors, and they are commonly used in obstacle detection systems (such as in robots).

### Passive IR sensor
Passive infrared (PIR) sensors detect infrared radiation but do not emit it via an LED. PIR sensors are most typically utilized for motion detection in home security systems.

![PIR](/Overview%20of%20the%20Arduino%20Components.md/PIR.PNG)

moving item emitting infrared radiation approaches the detector's detecting range, the IR level difference between the two pyroelectric elements is monitored.

The sensor subsequently transmits an electrical signal to an embedded computer, which activates an alert.

## Working of IR sensor module

![IR](/Images/IRS.PNG)

As we know till now that the active IR Sensors emit Infrared waves and as-well-as detect the Infrared ways.

The IR sensor module exactly works on the same phenomenon. The IR Sensor module contains an Infrared LED and an infrared photodiode. 

**Infrared LED**

The Infrared LED looks the same as a normal LED. But the Infrared LED emits light that is invisible to the naked eyes.

Whenever the electricity is given to the Infrared LED. it emits infrared light.

**Infrared Photodiode**

The IR photodiode will be black in color as shown in the picture above. Whenever Infrared waves are applied to the Infrared photodiode, in result the Infrared photodiode changes its resistance, which causes a change in the output voltages.

## Supplies needed

- Arduino 
- Jumper wires
- IR sensor module

## Wiring

- Vcc to 5V
- GND to GND
- OUT TO Digital pin (2)

![IR](/Images/IR.PNG)

## Arduino Sketch

```C++

int irSensorPin = 2;   // IR Sensor connected to digital pin 2

void setup() {
  pinMode(irSensorPin, INPUT);  // Set the IR sensor pin as input

 Serial.begin(9600);   // Initialize the serial communication at 9600 baud rate
}

void loop() {
  int sensorState = digitalRead(irSensorPin); // Read the state from the IR sensor

  
  delay(100);  // Wait for 100 milliseconds
}

```