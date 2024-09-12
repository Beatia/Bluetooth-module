# Bluetooth-module for LED
#include <SoftwareSerial.h>

SoftwareSerial HC(10, 11); 

int LED = 7;

int val;

void setup()

{

  Serial.begin(9600);

  HC.begin(9600);

  Serial.println("Pairing key is 0000 or 1234.");

  pinMode(LED, OUTPUT);

}

void loop()

{

  if (HC.available()) {

    val = HC.read();

    if (val == '1') {

      digitalWrite(LED, 1);

      HC.println("LED ON");

    }

    else if (val == '0') {

      digitalWrite(LED, 0);

      HC.println("LED Off ");

    }

    else HC.println("Enter 0 for off or 1 for on :)"); 

  }

}
