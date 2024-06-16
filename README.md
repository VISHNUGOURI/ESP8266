#include <SoftwareSerial.h>

// Define software serial ports for ESP8266 communication
SoftwareSerial esp8266(2, 3); // RX, TX

void setup() {
  Serial.begin(9600); // Serial monitor
  esp8266.begin(9600); // ESP8266 module

  Serial.println("Initializing ESP8266 communication...");
  esp8266.println("AT"); // Send AT command
}

void loop() {
  if (esp8266.available()) {
    Serial.write(esp8266.read()); // Print response from ESP8266 to serial monitor
  }

  if (Serial.available()) {
    esp8266.write(Serial.read()); // Send data from serial monitor to ESP8266
  }
}
