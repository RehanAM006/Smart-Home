# 🏠 Smart Home System using ESP8266, Blynk, DHT11 & MQ2

A Wi-Fi-enabled **Smart Home Automation and Safety System** built using the **ESP8266** microcontroller and **Blynk IoT** platform.

The system combines environmental monitoring, gas/smoke detection, appliance control, automated doors, and emergency alarms into a single IoT solution that can be monitored and controlled remotely.

## 📌 Project Overview

The Smart Home System provides both **home automation** and **safety monitoring**.

An ESP8266 acts as the main controller and communicates with sensors and actuators while connecting to the Blynk platform over Wi-Fi.

Users can monitor temperature, humidity, and gas levels and remotely control lights and doors through the Blynk interface.

If dangerous gas or smoke levels are detected, the system can activate a buzzer alarm and trigger emergency actions such as opening doors.

## ✨ Features

### 🌡️ Temperature & Humidity Monitoring

A **DHT11 sensor** continuously measures:

* Temperature
* Humidity

The measurements can be displayed remotely through the Blynk dashboard.

### 🔥 Gas & Smoke Detection

An **MQ2 gas sensor** monitors the environment for gases and smoke.

It can detect substances such as:

* LPG
* Smoke
* Methane
* Other combustible gases

When the sensor reading exceeds the configured safety threshold, the system enters an alarm state.

### 🚨 Emergency Alarm

When unsafe gas levels are detected, the system can:

* Activate the buzzer
* Update the alarm status on Blynk
* Trigger a Blynk event/notification
* Automatically open configured doors for emergency ventilation or evacuation

### 💡 Remote Light Control

Lights or other suitable appliances can be connected through a **relay module**.

The Blynk dashboard allows the user to remotely switch these devices **ON/OFF** over Wi-Fi.

### 🚪 Front Door Control

A servo motor controls the front door.

The door can be opened or closed remotely through Blynk.

### 🚗 Garage Door Control

A second servo can be used to automate the garage door.

Users can remotely control its position through the Blynk interface.

## 🛠️ Hardware Requirements

| Component      | Purpose                             |
| -------------- | ----------------------------------- |
| ESP8266        | Main Wi-Fi microcontroller          |
| DHT11          | Temperature and humidity monitoring |
| MQ2            | Gas and smoke detection             |
| Servo Motor ×2 | Front and garage door control       |
| Relay Module   | Light/appliance control             |
| Buzzer         | Gas/smoke alarm                     |
| Jumper Wires   | Circuit connections                 |
| Breadboard     | Prototyping                         |
| Power Supply   | Power for ESP8266 and peripherals   |

## 💻 Software Requirements

* Arduino IDE
* ESP8266 Board Package
* Blynk Library
* DHT Sensor Library
* Servo Library / ESP8266-compatible servo library

## 🧠 System Architecture

```text
                 ┌─────────────────┐
                 │    Blynk IoT    │
                 │   Mobile/Web    │
                 └────────┬────────┘
                          │
                        Wi-Fi
                          │
                  ┌───────▼───────┐
                  │    ESP8266    │
                  └───────┬───────┘
                          │
          ┌───────────────┼────────────────┐
          │               │                │
       DHT11             MQ2            Relay
          │               │                │
    Temperature       Gas/Smoke          Light
     & Humidity         Level            Control
                          │
                       Alarm
                          │
                       Buzzer

                  ┌───────┴───────┐
                  │               │
              Door Servo      Garage Servo
```

## ⚙️ How It Works

1. The **ESP8266 connects to Wi-Fi and Blynk**.
2. The **DHT11** measures temperature and humidity.
3. The **MQ2** continuously monitors the gas/smoke level.
4. Sensor readings are sent to the Blynk dashboard.
5. Blynk controls allow the user to operate lights and doors remotely.
6. If the MQ2 reading exceeds the configured threshold:

   * The buzzer activates.
   * The system reports an alarm state.
   * A Blynk event/notification can be generated.
   * Configured doors can automatically open.
7. Once conditions return to a safe state, the system can return to normal operation.

## 📱 Blynk Dashboard

The Blynk dashboard can contain widgets for:

| Widget      | Function                     |
| ----------- | ---------------------------- |
| Temperature | Display DHT11 temperature    |
| Humidity    | Display DHT11 humidity       |
| Gas Level   | Display MQ2 reading          |
| Light       | ON/OFF control               |
| Front Door  | Open/Close control           |
| Garage Door | Open/Close control           |
| Gas Alarm   | Display warning/alarm status |

Virtual pins can be assigned according to the implementation used in the Arduino sketch.

## 📂 Suggested Repository Structure

```text
Smart-Home-ESP8266/
│
├── src/
│   └── smart_home.ino
│
├── images/
│   ├── circuit-diagram.png
│   └── blynk-dashboard.png
│
├── README.md
├── LICENSE
└── .gitignore
```

## 🔐 Configuration

Before uploading the program to the ESP8266, configure your Wi-Fi and Blynk credentials.

```cpp
#define BLYNK_TEMPLATE_ID "YOUR_TEMPLATE_ID"
#define BLYNK_TEMPLATE_NAME "Smart Home"

char auth[] = "YOUR_BLYNK_AUTH_TOKEN";
char ssid[] = "YOUR_WIFI_NAME";
char pass[] = "YOUR_WIFI_PASSWORD";
```

> **Important:** Do not upload real Wi-Fi passwords or Blynk authentication tokens to a public GitHub repository.

Consider storing credentials in a separate `secrets.h` file and adding it to `.gitignore`.

## 🔄 System Flow

```text
Power ON
   │
   ▼
Initialize ESP8266
   │
   ▼
Connect to Wi-Fi
   │
   ▼
Connect to Blynk
   │
   ▼
Read DHT11 + MQ2
   │
   ├──── Send sensor values to Blynk
   │
   ▼
Is Gas Level > Threshold?
   │
   ├── NO ──► Normal Operation
   │
   └── YES
        │
        ├── Activate Buzzer
        ├── Trigger Blynk Alert
        └── Perform Emergency Door Action
```

## ⚠️ Safety Notice

This project is intended for **educational and prototype purposes**.

MQ2 modules and hobby-grade microcontrollers should **not be treated as certified replacements for commercial smoke, fire, carbon-monoxide, or gas-leak alarms**. Safety-critical home installations should use appropriately certified detection and alarm equipment.

## 🚀 Possible Future Improvements

* Replace DHT11 with DHT22/BME280 for improved environmental measurements
* Add flame detection
* Add PIR motion sensors
* Add smart locks
* Add an OLED/LCD status display
* Add power consumption monitoring
* Add automatic exhaust-fan control
* Add historical sensor data
* Add additional rooms and appliances
* Integrate voice assistants
* Add backup power for emergency operation

## 🎯 Applications

This project demonstrates concepts related to:

* Internet of Things (IoT)
* Smart home automation
* Wireless sensor networks
* Environmental monitoring
* Embedded systems
* ESP8266 development
* Remote device control
* Basic home safety automation

## 📄 License

This project may be used for educational and learning purposes. Add an appropriate open-source license such as the **MIT License** if you intend to distribute or allow reuse of the source code.

---

**Smart Home System — ESP8266 + Blynk + DHT11 + MQ2**

An IoT-based approach to home monitoring, automation, and safety.
