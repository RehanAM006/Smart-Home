Smart Home System with ESP8266, Blynk, DHT11, and MQ2 Sensor
Project Overview:
This project aims to create a smart home system that integrates various sensors and actuators using the ESP8266 microcontroller. The system includes temperature monitoring, gas detection, and remote control of home appliances such as lights and doors. The Blynk platform is used to provide a user-friendly interface for monitoring and controlling the system.

-Features:
Temperature Monitoring: Uses a DHT11 sensor to measure temperature and humidity. The readings are displayed on the Blynk app.
Gas Detection: Employs an MQ2 sensor to detect gas levels (e.g., smoke, LPG, CO). If the gas level exceeds a predefined threshold, an alarm is triggered, and notifications are sent via Blynk.
Remote Control of Lights: Allows the user to turn lights on or off through the Blynk app.
Automated Door Control: Utilizes servos to open and close the front door and garage door. These can be controlled remotely via Blynk or automatically opened in case of a gas alarm.
Buzzer Alarm: Activates a buzzer when the gas level exceeds the safe threshold.
-Hardware Components:
ESP8266 microcontroller
DHT11 temperature and humidity sensor
MQ2 gas sensor
Servos (for door and garage door control)
Relay module (for light control)
Buzzer
Connecting wires
-Software Components:
Arduino IDE
Blynk Library
DHT Library
Servo Library
