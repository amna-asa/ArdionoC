# Ultrasonic Sensor

The Ultrasonic sensor is also known as sonar sensor. It is used to measure distance. It sends out sound waves and measures how long they take to bounce back, helping to figure out how far away an object is.  

## How does the HC-SR04 Ultrasonic Distance Sensor Works?

It emits an ultrasound at 40,000 Hz that travels through the air. If there is an object or obstacle in its path, the sound will bounce back to the module. By measuring the travel time and knowing the speed of sound, you can calculate the distance.  

![calculation](/Images//working.PNG)  

To generate the ultrasound, we need to set the Trig pin to a High state for 10 µs. This action sends out an 8-cycle ultrasonic burst that travels at the speed of sound. Immediately after the burst is sent, the Echo pin goes High and starts listening for the wave to be reflected back from an object.  

*If there is no object or reflected pulse, the Echo pin will time-out after 38ms and get back to low state.*

## Connections
The sensor has 4 pins: VCC, GND, Trig, and Echo.  
- VCC and GND:   
  - Connect to the 5V and GND pins on the Arduino, respectively.  
- Trig and Echo:  
  - Connect to any digital Arduino pin.  
    **Trig:** Used to send the ultrasound wave from the transmitter.   
**Echo:** Used to listen for the reflected signal.  

*It will come out like shown below*  

![calculation](/Images//wiring.PNG)  

> #### Formula for measuring distance  
>Distance = (Speed x Time) / 2 = (34cm/ms x 1.5ms) / 2 = 25.5cm.  

![formula](/Images/calculation.PNG)   

When we measure how long the Echo pin was active, we can determine the distance the sound traveled from the sensor to the object.

To find this distance, we use a simple formula:

**Distance = Speed x Time**

For instance, if the Echo pin was active for 2 milliseconds, and we want the result in centimeters, we can change the speed of sound from 340 meters per second to 34 centimeters per millisecond.

So, the distance equals:

**Distance = (Speed x Time) / 2 = (34cm/ms x 1.5ms) / 2 = 25.5cm.**

## Arduino Sketch  
 ```C++
 int trigPin = 9;
int echoPin = 8;
int ledPin = 7;
int duration;
float distance;

void setup(){
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(ledPin, OUTPUT);

  Serial.begin(9600);
}

void loop()
{
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin, HIGH);
  distance = duration * 0.034 / 2;

  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");

  delay(500); // Delay to avoid serial monitor flooding
}
 ```
