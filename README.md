
# 🚦 IoT-Based Traffic Management System

This project is an **IoT-based traffic control and access management system** that uses **RFID** and **ultrasonic sensors** to manage vehicle entry and simulate traffic light behavior. It consists of two Arduino sketches: one for **gate access control** using RFID and distance sensors, and another for **traffic signal simulation**.

How to run the project:

## 📁 Project Files

- `multriultrarfid.ino` — Manages **RFID-based gate access** with distance sensing and servo control.
- `tlcheck.ino` — Simulates a **traffic signal** system using LEDs and sensor inputs.

---

## ⚙️ Hardware Requirements

- Arduino Uno or Nano
- HC-SR04 Ultrasonic Sensors × 2
- MFRC522 RFID Reader
- RFID Tags or Cards
- Servo Motor (for gate simulation)
- LEDs (Red, Yellow, Green)
- Resistors (220Ω for LEDs)
- Breadboard and jumper wires
- USB cable and 5V power supply
Spaces
---
## 🛠️ Setup Instructions

### 1. Wiring

#### 🔐 RFID + Gate Access (`multriultrarfid.ino`)
- Connect the MFRC522 to Arduino via SPI:
  - **SDA** → Pin 10  
  - **SCK** → Pin 13  
  - **MOSI** → Pin 11  
  - **MISO** → Pin 12  
  - **RST** → Pin 9  
  - **3.3V & GND** as required
- Connect Servo signal wire to Pin 8
- Connect ultrasonic sensors to trigger and echo pins as defined in the code


STEP BY STEP SOFTWARE EXECUTION

1. Install Required Software
Make sure you have Python installed on your machine. You can download Python from the official website.

You’ll also need some libraries to simulate the traffic management system:

RPi.GPIO (to simulate hardware GPIO pins, used for LEDs and sensor control)

time (for delays and timing logic)

threading (for handling concurrent tasks like sensor reading and traffic light management)
2. Simulate the RFID Reader (Using Python)
Since we cannot use an actual RFID reader in the software, we can simulate the reading process by prompting the user for input (simulating RFID tag scans).

3. Simulate Ultrasonic Sensor for Traffic Light Control
For the ultrasonic sensor, you can use a random number generator or simulate distance measurements to control the traffic light.

Explanation of the Code
Traffic Light Simulation: The TrafficLight class manages the traffic light state. It can switch between RED, YELLOW, and GREEN states. The run() method simulates the changing of lights every 5 seconds.

RFID Reader Simulation: The RFIDReader class simulates RFID tag reading by asking the user to input a tag number. It checks if the entered tag matches a predefined list of tags.

Ultrasonic Sensor Simulation: The UltrasonicSensor class simulates the measurement of distance by generating random values between 1 and 100 cm. If the distance is less than 10 cm, it triggers a change in the traffic light.

Concurrency: The program runs the traffic light in a separate thread while continuously checking for RFID scans and object detection via the ultrasonic sensor. This mimics how the system would work in a real-world scenario.



#### 🚦 Traffic Signal (`tlcheck.ino`)
- Red LED → Digital Pin 2  
- Yellow LED → Digital Pin 3  
- Green LED → Digital Pin 4  
- Use resistors to limit current to LEDs
- Optional: Additional sensor for traffic detection

### 2. Install Required Libraries

In Arduino IDE:

- Go to **Sketch > Include Library > Manage Libraries**
- Search for and install:
  - `MFRC522` by GithubCommunity
  - `Servo` by Arduino

### 3. Upload the Code

- Open **`multriultrarfid.ino`** in Arduino IDE
  - Connect your Arduino and select the correct COM port
  - Click **Upload**
- Then open **`tlcheck.ino`** and upload it to a second Arduino board (if using two systems), or run them separately for simulation

---

## 🧠 How It Works

### RFID Gate System
- Vehicle arrives and is detected by an **ultrasonic sensor**
- The driver scans an **RFID tag**
- If valid and within distance, the **servo motor opens the gate**

### Traffic Light System
- Cycles through **Red → Yellow → Green**
- LED delays simulate real-world timing
- Can be extended to react based on vehicle presence using a sensor

---

## 🧪 Testing

1. Open **Serial Monitor** (9600 baud) to check RFID detection and distance values.
2. Place an object in front of the ultrasonic sensor and scan an RFID tag.
3. Observe gate opening (servo rotation) and LED traffic light cycling.

---

## 📌 Notes

- Use a second Arduino if you want both systems (traffic signal and gate control) running simultaneously.
- Modify the RFID UID list in `multriultrarfid.ino` to accept your own cards.
- Calibrate ultrasonic sensors for accurate distance detection if needed.

---

## 📷 Demo / Future Work

> *[Optional: Add pictures or a link to a demo video here]*

- Add IoT integration (e.g., ESP8266 for online monitoring)
- Store logs of RFID scans using EEPROM or cloud
- Add pedestrian signals or more complex traffic logic

---

## 📍 Author

Made with 💡 for smart city innovations and embedded system learning.

