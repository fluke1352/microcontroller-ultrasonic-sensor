## อุปกรณ์วัดส่วนสูงแบบกะทัดรัด
## บทนำ






## อุปกรณ์



## ผังงาน




## โค้ด
~~~~~~~~~
 #include <NewPing.h>
 #include "SevenSegmentTM1637.h"

 const int trigPin = 12;
 const int echoPin = 11;
 const int speakerPin = 7;
 const byte PIN_CLK = A4;
 const byte PIN_DIO = A5;
 SevenSegmentTM1637    display(PIN_CLK, PIN_DIO);
 
long duration;
int distance;
int beepCount = 0;
 
void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(speakerPin, OUTPUT);
  display.begin();
  display.setBacklight(100);
  display.print("INIT");
  delay(1000);
  Serial.begin(9600);
}
 
void loop() {
   
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
 
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
 
  duration = pulseIn(echoPin, HIGH);
 
  distance = duration * 0.034 / 2;
 
  Serial.print("Distance: ");
  Serial.println(distance);
  display.clear();
  if (distance > 500){
    display.print("NOPE");
    }
  else{display.print(distance);}
}
~~~~~~~~~
