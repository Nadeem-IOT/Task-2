# DC Motor Speed Control & Obstacle Avoidance

##Project Description
This project controls the speed of a DC Motor using Pulse Width Modulation (PWM) and automatically halts the motor when an ultrasonic sensor (HC-SR04) detects an obstacle closer than 20 cm. Built and simulated on Tinkercad as part of my Internspark internship.

---

##  Components Used
* Arduino Uno R3
* Breadboard
* HC-SR04 Ultrasonic Distance Sensor
* L293D Motor Driver IC
* DC Motor

---

##  Circuit Connection details

### 1. HC-SR04 Sensor to Arduino
* **VCC** ➡️ Breadboard Power Rail (+5V)
* **Trig** ➡️ Arduino Digital Pin 2
* **Echo** ➡️ Arduino Digital Pin 3
* **GND** ➡️ Breadboard Ground Rail (GND)

### 2. L293D Motor Driver to Arduino
* **Pin 1 (Enable 1,2)** ➡️ Arduino Digital Pin 5 (Hardware PWM pin)
* **Pin 2 (Input 1)** ➡️ Arduino Digital Pin 4
* **Pin 7 (Input 2)** ➡️ Arduino Digital Pin 7
* **Pins 4 & 5 (GND)** ➡️ Breadboard Ground Rail (GND)
* **Pins 8 & 16 (VCC)** ➡️ Breadboard Power Rail (+5V)

---

##  Test Results (Distance vs Response)

| Distance Measured (cm) | Motor State | Motor Speed (RPM) | System Status |
|------------------------|-------------|-------------------|---------------|
| 60 cm                  | RUNNING     | Positive RPM      | Path Clear    |
| 40 cm                  | RUNNING     | Positive RPM      | Path Clear    |
| 15 cm                  | STOPPED     | 0 RPM             | Obstacle!     |
| 8 cm                   | STOPPED     | 0 RPM             | Obstacle!     |

---





---

##  Developer
* **Name:** Sayyad Nadeem
* **Internship:** Internspark IoT/Embedded Systems Intern