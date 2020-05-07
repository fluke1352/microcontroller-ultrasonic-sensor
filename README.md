## อุปกรณ์วัดส่วนสูงแบบกะทัดรัด
[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/VHUgNPPt1yw/0.jpg)](https://www.youtube.com/watch?v=wkeyyy1Nvvw)
## บทนำ
ปัจจุบันอุปกรณ์ที่ใช้วัดค่าต่างๆ สามารถหาได้ยากขึ้น ในที่นี้พวกเราสนใจในเรื่องของการวัดค่าส่วนสูงต่างๆ ในปัจจุบันอุปกรณ์บางชนิดที่ใช้ในการวัดค่าส่วนสูง อาจมีข้อผิดพลาดในการทำงาน เช่น คำนวณผิดพลาด ได้ค่าไม่ตรงกับความเป็นจริง พวกเราจึงจัดทำอุปกรณ์วัดค่าส่วนสูง สามารถใช้งานได้อย่างดายและสะดวกกะทัดรัดง่ายต่อการพกาพ ผลการทดลองออกมาเป็นที่น่าพอใจ ได้ค่าที่มีความแม่นยำ และใกล้เคียงกับความเป็นจริง

## อุปกรณ์
1.ultrasonic sensor รุ่น HC-SR04

![MICROCONTROLLERULTRASONICSENSORSCHEMATIC](https://gb.lnwfile.com/ir48b6.png)

2.บอร์ด arduino uno

![MICROCONTROLLERULTRASONICSENSORSCHEMATIC](https://o.lnwfile.com/g04196.jpg)

3.7 segment 4 digit

![MICROCONTROLLERULTRASONICSENSORSCHEMATIC](https://ae01.alicdn.com/kf/HTB1nAEtc7voK1RjSZFNq6AxMVXat/Tm1637-4-led-0-56-0-56-7-arduino.jpg)
4.Jumper Arduino
![MICROCONTROLLERULTRASONICSENSORSCHEMATIC](https://cu.lnwfile.com/ea1jr8.jpg)


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
## หัวข้อหลักการทำงาน
![MICROCONTROLLERULTRASONICSENSOR2](https://user-images.githubusercontent.com/56569795/81039242-ac1bc980-8ed2-11ea-9109-f7a6e7ccab23.jpg)
## ภาพ
![MICROCONTROLLERULTRASONICSENSOR](https://user-images.githubusercontent.com/56569795/81038956-e0db5100-8ed1-11ea-908e-b02f21f80e4b.jpg)

## สมาชิก
  | 62070008| 62070032 | 62070061 | 62070171 |
  | --- | --- | --- | --- |
  |  นายกวิน ลิมะวรารัตน์ | นายจิรายุ ทับทิมทอง | นายณัฐชนน อำนาจทอง |  นายวุฒิ จารุสุภัทร |
  
