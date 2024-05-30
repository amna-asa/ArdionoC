# Simple LED control

An LED light works with Arduino by sending digital signals. When the signal is high, the LED turns on, and when the signal is low, the LED turns off. The digitalWrite() function can mimic this behavior. For example, digitalWrite(LED, HIGH) sends a 5V current through the digital pin, while digitalWrite(LED, LOW) sends a 0 current. The delay() function controls the transition between the on and off stages.

![LED](/Images/LED.PNG)

# Arduino sketch
```C++
int ledPin = 5;                                               // Define the pin number for the LED


void setup() {                                               // Setup runs once when the Arduino is powered on or reset
 
  pinMode(ledPin, OUTPUT);                                  // Initialize the digital pin as an output
}


void loop() {                                               // Loop runs continuously after setup
  
  digitalWrite(ledPin, HIGH);                              // Turn the LED on (HIGH) for 1 second
  delay(1000);                                               // Wait for 1000 milliseconds (1 second)
  
 
  digitalWrite(ledPin, LOW);                                  // Turn the LED off (LOW) for 1 second
  delay(1000);                                               // Wait for 1000 milliseconds (1 second)
}

```