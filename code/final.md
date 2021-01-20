#define echoPin 11
#define trigPin 12
#define potPin0 0
#define potPin1 1
#define potPin2 2
#define potPin3 3
#define potPin4 4
#define potPin6 6


int maxRange = 200;
int minRange = 0;
int val0 = 0;
int val1 = 0;
int val2 = 0;
int val3 = 0;
int val4 = 0;
int val5 = 0;
int val6 = 0;
int val7 = 0;
long duration, distance;


void setup() {
  Serial.begin(9600);
  pinMode(trigPin,OUTPUT);
  pinMode(echoPin,INPUT);
  pinMode(potPin0,INPUT);
  pinMode(potPin1,INPUT);
  pinMode(potPin2,INPUT_PULLUP);
  pinMode(potPin3,INPUT);
  pinMode(potPin4,INPUT);
  pinMode(potPin6,INPUT);
  pinMode(A2,INPUT);
  
}

void loop() {
 val0 = analogRead(A0);
 val1 = analogRead(A1);
 val2 = digitalRead(2);
 val3 = analogRead(A3);
 val4 = analogRead(A4);
 val6 = digitalRead(6);
 val7 = analogRead(A2);
 digitalWrite(trigPin,LOW);
 delayMicroseconds(2);

 digitalWrite(trigPin,HIGH);
 delayMicroseconds(10);

 digitalWrite(trigPin,LOW);
 duration = pulseIn(echoPin,HIGH);

 distance = duration / 58.2;
 val5 = distance;

 if(distance >= maxRange || distance <= minRange) {
  Serial.print(val0);
   Serial.print(" ");
   Serial.print(val1);
   Serial.print(" ");
   Serial.print(val2);
   Serial.print(" ");
   Serial.print(val3);
   Serial.print(" ");
   Serial.print(val4);
   Serial.print(" ");
   Serial.print("-20");
   Serial.print(" ");
   Serial.print(val6);
   Serial.print(" ");
   Serial.println(val7);
  
 }else {
   Serial.print(val0);
   Serial.print(" ");
   Serial.print(val1);
   Serial.print(" ");
   Serial.print(val2);
   Serial.print(" ");
   Serial.print(val3);
   Serial.print(" ");
   Serial.print(val4);
   Serial.print(" ");
   Serial.print(val5);
   Serial.print(" ");
   Serial.print(val6);
   Serial.print(" ");
   Serial.println(val7);
  
  }

  delay(50);
 


}