## อุปกรณ์วัดส่วนสูงแบบกะทัดรัด
## บทนำ
![MICROCONTROLLERULTRASONICSENSOR2](https://user-images.githubusercontent.com/56569795/81039242-ac1bc980-8ed2-11ea-9109-f7a6e7ccab23.jpg)






## อุปกรณ์



## ผังงาน
![MICROCONTROLLERULTRASONICSENSORSCHEMATIC](https://user-images.githubusercontent.com/56569795/81039152-63641080-8ed2-11ea-84a2-0c6badaa1189.jpg)
![MICROCONTROLLERULTRASONICSENSORSCHEMATIC2](https://user-images.githubusercontent.com/56569795/81039161-6c54e200-8ed2-11ea-9ba5-a45be2c0bdff.jpg)




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
## ภาพ
![MICROCONTROLLERULTRASONICSENSOR](https://user-images.githubusercontent.com/56569795/81038956-e0db5100-8ed1-11ea-908e-b02f21f80e4b.jpg)
