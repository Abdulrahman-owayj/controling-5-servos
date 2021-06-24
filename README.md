# Controling 5 servos projects
Here I used the Arduino devolvement board for three project:

**1 - control 5 servos to move 90 degree when turned on**

The circuit was designed using tinkercad website, you can reffer to the picture for the connection and see the code below.

```ruby
#include <Servo.h>;
Servo mservo;
Servo mservo1;
Servo mservo2;
Servo mservo3;
Servo mservo4;

void setup() {
  
  pinMode(2, OUTPUT);
  pinMode(3, OUTPUT);
  pinMode(4, OUTPUT);
  pinMode(5, OUTPUT);
  pinMode(6, OUTPUT);
  
  mservo.attach(2);
  mservo1.attach(3);
  mservo2.attach(4);
  mservo3.attach(5);
  mservo4.attach(6);
}
void loop() {
  mservo.write(90);
  mservo1.write(90);
  mservo2.write(90);
  mservo3.write(90);
  mservo4.write(90);
}
```

**2 - control 5 servo using 5 potentiameter (variable resistance)**

Here i used 5 varibale resistances to controll 5 servos using the arduino as a controller, you can see picture of the circuit diagram provided in this repositry and asee the code attached below (make sure to have the servo library installed)

Link for tinkercard project : https://www.tinkercad.com/things/dPAHhonEyF1-editing-components/editel?lessonid=EFU6PEHIXGFUR1J&projectid=OIYJ88OJ3OPN3EA&collectionid=OIYJ88OJ3OPN3EA&tenant=circuits

```ruby
#include <Servo.h>; 

// creating a servo objects
Servo mservo;
Servo mservo1;
Servo mservo2;
Servo mservo3;
Servo mservo4;

// defining variable for the input pin and to store the input value
int s;      int potinput = A1;
int s1;     int potinput1 = A2;
int s2;     int potinput2 = A3;
int s3;     int potinput3 = A4;
int s4;     int potinput4 = A5;

// define the output pin numbers
int servpin = 3;
int servpin1 = 5;
int servpin2 = 6;
int servpin3 = 10;
int servpin4 =11;

void setup() {
 // set the pinMode as output
  pinMode(servpin, OUTPUT);
  pinMode(servpin1, OUTPUT);
  pinMode(servpin2, OUTPUT);
  pinMode(servpin3, OUTPUT);
  pinMode(servpin4, OUTPUT);
  
// attach the servo object with each pin
  mservo.attach(servpin);
  mservo1.attach(servpin1);
  mservo2.attach(servpin2);
  mservo3.attach(servpin3);
  mservo4.attach(servpin4);
}

void loop() {
   // store the input in each variable
  s  = analogRead(potinput);
  s1 = analogRead(potinput1);
  s2 = analogRead(potinput2);
  s3 = analogRead(potinput3);
  s4 = analogRead(potinput4);
  
  // remap the values to degree range which is 0 - 180
  s = map(s, 0, 1023, 0, 180);
  s1 = map(s1, 0, 1023, 0, 180);
  s2 = map(s2, 0, 1023, 0, 180);
  s3 = map(s3, 0, 1023, 0, 180);
  s4 = map(s4, 0, 1023, 0, 180);
  
  //give the order to move to the servo for each pin
  mservo.write(s);
  mservo1.write(s1);
  mservo2.write(s2);
  mservo3.write(s3);
  mservo4.write(s4);
  
  // small delay for the servo movment
  delay(15);
}
```

**3-  using potentiometer to control a servo (physically)**

For this project i just provided a video of the same circuit (controlling one servo using one variable resistance using arduino) you can use the same circuit diagram and the same code of the second project which using 5 servos and 5 resiatances but you need to make sure to adjust the pin number and delete the code part of the rest of the servos.
