# 🗑️ Smart Dustbin using Arduino (9th Grade Project)

🏆 **Prize Winner**: This project won **1st Prize** at the *Explorica'23* science exhibition in our school!

This is an Arduino-based smart, contactless dustbin that automatically opens its lid when it detects an object nearby. I built this project back in 9th grade with my friend Bhairavi Ghodmare using a YouTube tutorial.

## 🚀 Project Overview
I built this project to promote better hygiene through touchless technology. By using an ultrasonic sensor to measure distances, the bin detects when a user approaches and triggers a servo motor to smoothly open the lid, closing it automatically after a brief delay.

## 🛠️ Tech Stack & Hardware
* **Microcontroller**: Arduino Uno (or compatible board)
* **Sensors**: HC-SR04 Ultrasonic Sensor
* **Actuators**: Servo Motor (e.g., SG90)
* **Language**: C++ / Arduino Wire Language
* **Learning Source**: YouTube tutorials & school lab sessions

## 📌 Pin Configurations

| Component | Arduino Pin |
| :--- | :--- |
| **Ultrasonic Trig** | Pin 5 |
| **Ultrasonic Echo** | Pin 6 |
| **Servo Signal** | Pin 7 |

## 💻 Code Structure & Logic
The embedded code utilizes a smart filtering mechanism to prevent false triggers:
1. **`measure()`**: Triggers the ultrasonic sensor bursts to calculate distance in centimeters.
2. **`loop()`**: Samples three consecutive readings to calculate an average distance, actively smoothing out erratic sensor noise.
3. **Threshold Check**: If an object is detected within **50 cm**, the servo motor attaches, opens the lid, waits for 3 seconds, closes it, and detaches to save battery power.

Feel free to star ⭐ this repository to follow my developer journey from the very beginning!
