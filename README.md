# 🗑️ Smart Dustbin using Arduino

🏆 **1st Prize Winner — Explorica'23 Science Exhibition**

An Arduino-based **smart, contactless dustbin** that automatically opens its lid when an object or person is detected nearby. The project was built in **2023** with my friend **Bhairavi Ghodmare** as a school science exhibition project.

## 🚀 Project Overview

The Smart Dustbin uses an **ultrasonic sensor** to detect objects within a predefined distance. When an object comes within **50 cm**, an **servo motor** automatically opens the dustbin lid.

After a short delay, the lid closes automatically, allowing the bin to be used without touching it.

The project demonstrates how simple embedded systems can be used to improve **hygiene, convenience, and contactless interaction**.

## ✨ Features

* 🖐️ **Touchless operation**
* 📡 Ultrasonic-based object detection
* ⚙️ Automatic lid control using a servo motor
* 📊 Three distance readings are averaged to reduce sensor fluctuations
* ⏱️ Automatic closing after opening
* 🔋 Servo is detached when not in use

## 🛠️ Components Used

| Component                 |    Quantity |
| ------------------------- | ----------: |
| Arduino Uno               |           1 |
| HC-SR04 Ultrasonic Sensor |           1 |
| SG90 Servo Motor          |           1 |
| Resistor                  |           1 |
| Jumper Wires              | As required |
| Dustbin with movable lid  |           1 |

## 📌 Pin Configuration

| Component    | Arduino Pin |
| ------------ | ----------: |
| HC-SR04 Trig |       Pin 5 |
| HC-SR04 Echo |       Pin 6 |
| Servo Signal |       Pin 7 |

## 💻 How It Works

The system follows a simple detection-and-actuation process:

```text
        Object detected
              ↓
      Ultrasonic Sensor
              ↓
     Measure distance
              ↓
    Average 3 readings
              ↓
      Distance < 50 cm?
          ↙         ↘
        YES          NO
         ↓            ↓
   Servo activated   Continue
         ↓
     Lid opens
         ↓
     Wait 3 seconds
         ↓
     Lid closes
         ↓
   Servo detached
```

## 🧠 Code Logic

### `setup()`

The Arduino initializes:

* Serial communication
* Servo motor
* Ultrasonic sensor pins
* Initial servo position

The servo is initially positioned at `0°`, keeping the lid closed.

### `measure()`

The ultrasonic sensor sends a short trigger pulse and measures the time taken for the echo to return.

The distance is calculated using:

```cpp
dist = (duration / 2) / 29.1;
```

This converts the measured echo duration into an approximate distance in centimeters.

### Distance Averaging

Instead of relying on a single sensor reading, the program takes **three consecutive measurements**:

```cpp
for (int i=0; i<=2; i++) {
    measure();
    aver[i] = dist;
    delay(10);
}
```

The three readings are then averaged:

```cpp
dist = (aver[0] + aver[1] + aver[2]) / 3;
```

This helps reduce small fluctuations in ultrasonic sensor readings.

### Automatic Lid Control

When the measured distance is below **50 cm**:

```cpp
if (dist < 50)
```

the servo is activated.

The lid remains closed initially, then the servo moves to `150°` to open the lid:

```cpp
servo.write(0);
delay(3000);
servo.write(150);
```

Afterward, the servo is detached.

## 🔧 Technology Used

* **Microcontroller:** Arduino Uno
* **Programming:** Arduino C++ / Wiring
* **Sensor:** Ultrasonic Sensor
* **Actuator:** Servo Motor
* **Detection Method:** Ultrasonic distance measurement

## 🏆 Achievement

🥇 **1st Prize — Explorica'23 Science Exhibition**

This project was developed as a school-level science exhibition project and demonstrated the practical application of **Arduino, sensors, and automation** to create a simple contactless solution.

## 📚 Learning & Inspiration

The project was developed with the help of **YouTube tutorials and school laboratory sessions**. Building it provided hands-on experience with:

* Arduino programming
* Ultrasonic sensors
* Servo motor control
* Sensor data processing
* Basic embedded-system design
* Hardware-software integration

## 👩‍💻 Project Team

**Aditi Atrey**

**Bhairavi Ghodmare**

Built in **2023** for the **Explorica'23 Science Exhibition**.

---

⭐ If you find this project interesting, consider giving the repository a star!

