# Cognitive Gas Flow Security: Autonomous Sensing and Response

This README file provides a comprehensive overview of the IoT-enabled Gas Safety System project, developed by students at VIT-AP University.

##  проекта (Project Description)

[cite_start]Gas leakage in both domestic and industrial settings is a significant safety hazard that can lead to explosions, fires, and health risks[cite: 2]. [cite_start]Traditional safety systems often fall short due to their lack of real-time intervention, remote control capabilities, and accurate gas level tracking[cite: 3].

[cite_start]This project, "Cognitive Gas Flow Security," is an IoT-enabled system designed to overcome these limitations[cite: 4]. [cite_start]It integrates advanced sensors and cloud connectivity to provide a modern, reliable, and cost-effective solution for gas safety[cite: 4, 11]. [cite_start]The system uses an MQ2 sensor for leak detection, an HX711 load cell for precise gas level measurement, and a dual-microcontroller setup (ESP8266 and Arduino Uno) for robust performance[cite: 5, 12]. [cite_start]A web application powered by Firebase allows users to monitor gas levels in real-time, control the gas valve remotely, and receive emergency alerts[cite: 6].

## ❗ Problem Statement

The project addresses the following critical challenges in gas safety:
* [cite_start]**Delayed Leak Detection:** Manual inspections are infrequent, allowing leaks to go unnoticed for extended periods[cite: 43]. [cite_start]A 2022 apartment fire in Mumbai, for instance, was caused by a leak that was not detected for 72 hours[cite: 44].
* [cite_start]**Lack of Remote Intervention:** In an emergency, users are often unable to shut off the main gas valve remotely, which increases response time and potential damage[cite: 45].
* [cite_start]**Inaccurate Gas Level Tracking:** Standard analog gauges can have error margins of up to ±15%, leading to unexpected shortages and refill demands[cite: 47].
* [cite_start]**High Cost of Commercial Systems:** Industrial-grade safety systems can cost over $1,000, making them unaffordable for most households and small businesses[cite: 49, 50].

## ✨ Key Features

* [cite_start]**Real-Time Leakage Detection:** Utilizes an MQ2 sensor to detect hazardous gas concentrations (LPG, Methane) above 400 ppm[cite: 52].
* [cite_start]**Automated Valve Control:** A servo motor automatically closes the gas valve within 2 seconds of detecting a leak[cite: 7, 53].
* [cite_start]**Remote Monitoring & Control:** A Firebase-powered web application, "Gasoo," allows users to monitor gas levels and remotely open or close the valve from any location[cite: 6, 55].
* [cite_start]**Precision Gas Level Monitoring:** An HX711 load cell measures the cylinder's weight with ±1% accuracy, displaying the remaining gas as a user-friendly percentage[cite: 8, 56, 57].
* [cite_start]**Emergency Alert System:** Automatically sends SMS and email alerts to registered users during a gas leak and provides push notifications via the web app[cite: 60, 61].
* [cite_start]**Dual-Microcontroller Architecture:** The system leverages an ESP8266 for IoT and Wi-Fi tasks and an Arduino Uno for real-time sensor reading and control, ensuring low latency and high reliability[cite: 12, 13, 29].
* [cite_start]**High Reliability:** The system was rigorously tested, demonstrating a 99.8% success rate in leakage detection and remote control functionality[cite: 10, 16].

## ⚙️ System Architecture and Workflow

[cite_start]The system's design separates tasks between two microcontrollers to optimize performance[cite: 12].

* **Arduino Uno:** Dedicated to real-time operations. [cite_start]It continuously reads data from the MQ2 gas sensor and controls the servo motor for valve operations[cite: 63].
* **ESP8266 NodeMCU:** Manages all IoT-related tasks. [cite_start]It processes data from the HX711 weight sensor, handles Wi-Fi connectivity, and synchronizes all data with the Firebase Realtime Database[cite: 62].

**Workflow:**
1.  **Leak Detection:** The MQ2 sensor continuously monitors the environment. [cite_start]If gas concentration exceeds 400 ppm, it sends a high signal to the Arduino Uno[cite: 69].
2.  [cite_start]**Valve Closure:** The Arduino immediately triggers the servo motor to close the gas valve[cite: 70]. Simultaneously, it sends a signal to the ESP8266 about the leak status.
3.  [cite_start]**Data Sync & Alerts:** The ESP8266 pushes the leak status, valve status, and real-time weight data to the Firebase database[cite: 71, 119]. [cite_start]This triggers SMS/email alerts to the user[cite: 60].
4.  [cite_start]**Remote Access:** The user can monitor the gas level percentage, see the valve status (Open/Closed), and manually toggle the valve through the "Gasoo" web application[cite: 15, 71].

## 🛠️ Technology Stack

### Hardware Components
| Component       | Specifications                          | Purpose                                |
| --------------- | --------------------------------------- | -------------------------------------- |
| ESP8266 NodeMCU | Wi-Fi: 802.11 b/g/n, 17 GPIO pins       | IoT connectivity, data processing      |
| Arduino Uno     | Microcontroller: ATmega328P, Clock: 16MHz | Sensor data processing, motor control  |
| MQ2 Gas Sensor  | Detection Range: 300-10,000 ppm         | Leakage detection                      |
| HX711 Load Cell | Capacity: 30 kg, Accuracy: ±1%          | Gas level measurement                  |
[cite_start]*[cite: 65]*

### Software and Cloud
* [cite_start]**Backend:** Firebase Realtime Database [cite: 66]
* [cite_start]**Frontend:** React.js [cite: 67]
* [cite_start]**Firmware:** Arduino IDE [cite: 68]
* [cite_start]**API Communication:** Axios [cite: 67]

## 🖥️ Web Application Interface ("Gasoo")

The web interface provides a clean, user-centric dashboard with the following features:
* [cite_start]**System Status:** Shows whether the system is "Safe" or in an "Alert" state[cite: 75].
* [cite_start]**Gas Level:** Displays the remaining gas as a percentage with corresponding min/max weight values[cite: 72].
* [cite_start]**Valve Control:** Allows users to see the current valve status and toggle it between "Open" and "Closed"[cite: 134].
* [cite_start]**Gas Detection:** Confirms that no leaks are detected or shows an active alert with emergency actions if a leak occurs[cite: 135, 137].

![Web App Interface](https://i.imgur.com/k2H1ZcO.png)
[cite_start]*(Image based on Figure 2 in the project report [cite: 72])*

## 📊 Results

The system's performance was validated through rigorous testing:

| Test Case         | Parameter        | Result                  | Remarks                |
| ----------------- | ---------------- | ----------------------- | ---------------------- |
| Leakage Detection | 400 ppm          | Valve closed in 2000 ms | Threshold achieved     |
| Weight Accuracy   | 15 kg (50% full) | 14.98 kg (±0.02 kg)     | 99.8% accuracy         |
| Web App Latency   | Data sync        | <1.5 seconds            | Firebase optimization  |
[cite_start]*[cite: 73]*

## 🚀 Future Scope

Potential future enhancements for this project include:
1.  [cite_start]**Machine Learning Integration:** To predict gas usage patterns and provide proactive refill alerts[cite: 87].
2.  [cite_start]**Multi-Cylinder Support:** Expanding the system to monitor multiple cylinders simultaneously for industrial applications[cite: 88].
3.  [cite_start]**Solar Power Integration:** Adding solar panels to enable off-grid operation and improve energy efficiency[cite: 89].

## 🧑‍💻 Contributors

This project was submitted by:
* [cite_start]A. Sriram Chowdary (22BCE7334) [cite: 1]
* [cite_start]I.S.H Akanksh (22BCE8116) [cite: 1]
* [cite_start]S. Sujindra (22BCE9083) [cite: 1]
* [cite_start]P. Dwijesh Reddy (22BCE9104) [cite: 1]
* [cite_start]R. Nikhlesh (22BCE8410) [cite: 1]
* [cite_start]V. Mokshagna (22BCE7195) [cite: 1]

Under the guidance of **Prof. [cite_start]Edara Sreenivasa Reddy**[cite: 1].

---

*This README was generated based on the project report "Cognitive Gas Flow Security: Autonomous Sensing and Response" from VIT-AP University.*
