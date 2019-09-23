#include <AFMotor.h>            //adafruit motorshield library
#include <Servo.h>
AF_DCMotor motor(1,MOTOR12_1KHZ);
AF_DCMotor motor2(2,MOTOR34_1KHZ);


Servo s;

    
void setup() {
 motor.setSpeed(255);
 motor2.setSpeed(255);
 s.attach(9);
 pinMode(35,OUTPUT);
 pinMode(33,OUTPUT);
 pinMode(37,INPUT);
 digitalWrite(33,HIGH);
 int max = 20;
 int t; // t should be set according to the hardware used
 Serial.begin(9600);
}

void loop() {
     s.write(95); 
     check(); 
    if (CM>max){
   motor.run(FORWARD);
   motor2.run(FORWARD);
    }
 if(CM < max){
    motor.run(RELEASE);
    motor2.run(RELEASE);
    s.write(35);
    delay(500);
    K1 = check();
    delay(1000);
    s.write(155);
    delay(500);
    K2 = check(); 
    delay(500);
    
  if (k1 >= k2){
    motor.run(FORWARD);
    motor2.run(BACKWARD);
    delay(t);
    motor.run(RELEASE);
    motor2.run(RELEASE);
  }
  else{
    motor2.run(FORWARD);
    motor.run(BACKWARD);
    delay(t);
    motor.run(RELEASE);
    motor2.run(RELEASE);
  }
 }
}
long check() 
{
  long duration , cm;
  digitalWrite(35,LOW);
  delay(2);
  digitalWrite(35,HIGH);
  delay(10);
  digitalWrite(35,LOW);
  duration = pulseIn(37,HIGH);
  cm = mstocm(duration);
  return cm;
  delay(100); 
}
long mstocm(long ms){
  return ms/29/2;
}
