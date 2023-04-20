#include <Servo.h>

Servo myservo1;
Servo myservo2;
Servo myservo3;

//setup button A 
const int buttonAPin = 2; 
int buttonAState = 0; 
int lastButtonAState = 0;
bool A = false;

//setup button B 
const int buttonBPin = 13; int buttonBState = 0; int lastButtonBState = 0; bool B = false;

//setup button C
 const int buttonCPin = 12; int buttonCState = 0; int lastButtonCState = 0; bool C = false;

void setup() { 
  myservo1.attach(7); 
  myservo1.write(0);
  myservo2.write(0);
  myservo3.write(0);
  myservo2.attach(8);
  myservo3.attach(4);
  pinMode(buttonAPin, INPUT); 
  pinMode(buttonBPin, INPUT); 
  pinMode(buttonCPin, INPUT); 
  Serial.begin(9600); 
  Serial.println("Start Story"); }

void loop() { 
  

  buttonAState = digitalRead(buttonAPin);

// read button A 
if (buttonAState != lastButtonAState) { 
  if(buttonAState == HIGH) { 
    A = true;
   } 
}

if (digitalRead(buttonAPin) == HIGH) { 
  myservo1.write(180); 
  }

if (A == true) { 
  buttonBState = digitalRead(buttonBPin); 
  if (buttonBState != lastButtonBState) { 
    if (buttonBState == HIGH) { 
      B = true; 
    }
  } 
}

if (digitalRead(buttonBPin) == HIGH) { 
  myservo2.write(180); 
  } 

if (B == true) { 
  buttonCState = digitalRead(buttonCPin); 
  if (buttonCState != lastButtonCState) { 
    if (buttonCState == HIGH) { 
      C = true; 
    } 
  } 
}

if (digitalRead(buttonCPin) == HIGH) { 
  myservo3.write(180); 
}

if (C == true) { 
  Serial.println("The End"); }

lastButtonAState = buttonAState; 
lastButtonBState = buttonBState; 
lastButtonCState = buttonCState; 
}
