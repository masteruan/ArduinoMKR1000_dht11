/**************************************************************
 * Blynk is a platform with iOS and Android apps to control
 * Arduino, Raspberry Pi and the likes over the Internet.
 * You can easily build graphic interfaces for all your
 * projects by simply dragging and dropping widgets.
 *
 *   Downloads, docs, tutorials: http://www.blynk.cc
 *   Blynk community:            http://community.blynk.cc
 *   Social networks:            http://www.fb.com/blynkapp
 *                               http://twitter.com/blynk_app
 *
 * Blynk library is licensed under MIT license
 * This example code is in public domain.
 **************************************************************/

#define BLYNK_PRINT Serial    // Comment this out to disable prints and save space
#include <SPI.h>
#include <WiFi101.h>
#include <BlynkSimpleMKR1000.h>
#include <SimpleTimer.h>
#include "DHT.h"

#define DHTPIN 7     // what pin we're connected to
#define DHTTYPE DHT11   // DHT 11 
DHT dht(DHTPIN, DHTTYPE);
// You should get Auth Token in the Blynk App.
// Go to the Project Settings (nut icon).
char auth[] = "#######################";

SimpleTimer timer;

// Your WiFi credentials.
// Set password to "" for open networks.
char ssid[] = "#######################";
char pass[] = "#######################";

void TimerEvent()
{
  int h = dht.readHumidity();
  int t = dht.readTemperature();
  Blynk.virtualWrite(V2, h);
  Blynk.virtualWrite(V3, t);
}

void setup()
{
  Serial.begin(9600);
  //Blynk.begin(auth, ssid, pass);
  // Or specify server using one of those commands:
  //Blynk.begin(auth, ssid, pass, "blynk-cloud.com", 8442);
  Blynk.begin(auth, ssid, pass, "46.101.143.225", 8442);
  timer.setInterval(1000L, TimerEvent);
  dht.begin();
}

void loop()
{
  Blynk.run();
  timer.run();
}
