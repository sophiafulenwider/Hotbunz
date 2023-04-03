// Hotbunz
#include <Servo.h>

Servo myservo;

//setup button A
const int buttonAPin = 2;
int buttonAState = 0;
int lastButtonAState = 0;
bool A = false 

//setup button B
const int buttonBPin = 3;
int buttonBState = 0;
int lastButtonBState = 0;
bool B = false 


void setup() {
  myservo.attach(9); 
  pinMode(buttonAPin, INPUT);
  pinMode(buttonBPin, INPUT);
  Serial.begin(9600);
  Serial.println("Start Story");
}

void loop() {
  buttonAState = digitalRead(buttonAPin);
  
  // read button A
  if (buttonAState != lastButtonAState) {
    if(buttonAState == HIGH) {
     A = true;
    }
  }
  
  if (digitalRead(buttonAPin) == HIGH) {
    myservo.write(90); 
  } 
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
    myservo.write(90); 
  } 
}

  if (B == true) {
    Serial.println("The End");
  }
  
  lastButtonAState = buttonAState;
  lastButtonBState = buttonBState; 
}

