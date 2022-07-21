# Push-button-with-Relay-and-Transistor
task 1 week 2



## Introduction

This electronic circuit is used for robots to turn themselves on or off without human intervention






## Technologies


1- Arduino IDE 1.8.19 [To Download](https://www.arduino.cc/en/software)



2- AUTODESK TINKERCAD [To Download](https://www.tinkercad.com/)





## Components required



1. Arduino UNO
2. Push Button
3. jumper wirs
4. Transistor NPN
5. bettrey 5 volt 
6. LED Light
7. RELAY
8. Rsistor





## Connections


connecting Transistor Emitter to Relay and Base to Arduino Pin 2 and Collector to 5V in Arduino .

connecting Push Button to Pin 8 in Arduino and Terminal 1a to GNR and Terminal 2a to 5V in Arduino .

connecting Relay GNR to GNR in Arduino and to power supply .

connecting LED Light Termenal 1 to power supply and Terminal 2 to Relay ,






## Block diagram & simulation



 for watching simulation [OPEN](https://www.tinkercad.com/things/2lF6XQazBab-super-duup-elzing/editel?tenant=circuits)




![Super Duup-Elzing](https://user-images.githubusercontent.com/109243989/180101282-25084e5a-bfa2-4004-a548-c0b09f2df55c.png)
 
 
When the push button is pressed it turns on




![Super Duup-Elzing (1)](https://user-images.githubusercontent.com/109243989/180101435-5fa2e3fc-7f12-49ce-a4bb-d325b6fef6dc.png)


After 7 seconds  it will turn off by itself



### The code




int pinButton = 8;
int Relay = 2;
int stateRelay = LOW;
int stateButton;
int previous = LOW;
long time = 0;
long debounce = 100;


int stayON = 7000; //stay on for 5000 ms

void setup() {
  pinMode(pinButton, INPUT);
  pinMode(Relay, OUTPUT);
}

void loop() {
  stateButton = digitalRead(pinButton);  
  if(stateButton == HIGH && previous == LOW && millis() - time > debounce) {
    if(stateRelay == HIGH){
      digitalWrite(Relay, LOW);
    } else {

      
       digitalWrite(Relay, HIGH);
       delay(stayON);
       digitalWrite(Relay, LOW);
    }
    time = millis();
  }
  previous == stateButton;
}
