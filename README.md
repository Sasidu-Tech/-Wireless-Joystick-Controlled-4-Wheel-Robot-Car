🚗 Wireless Joystick-Controlled 4-Wheel Robot Car

A wireless 4-wheel robotic car controlled using an ESP32 + Arduino Joystick Module. The system uses ESP-NOW for fast wireless communication between the Joystick Unit (Transmitter) and the Car Unit (Receiver).

📌 Project Overview

This project consists of two ESP32 units:

🎮 Joystick Unit — Transmitter

- ESP32
- Arduino Joystick Module
- Reads X-axis, Y-axis, and Push Button (SW) values
- Sends movement commands wirelessly using ESP-NOW

🚗 Car Unit — Receiver

- ESP32
- L298N Motor Driver
- 4 DC Gear Motors
- 11.1V Li-ion Battery
- Receives commands from the Joystick Unit through ESP-NOW

⚙️ System Architecture

        🎮 JOYSTICK UNIT
       ESP32 + Joystick
              │
              │
          ESP-NOW
       Wireless Link
              │
              ▼
          🚗 CAR UNIT
            ESP32
              │
           L298N
              │
       ┌──────┴──────┐
       │             │
   Left Motors    Right Motors
    (Parallel)     (Parallel)
       │             │
       └──────┬──────┘
              ▼
          4-Wheel Drive

🔌 Joystick Unit Connections

Joystick Module| ESP32
VCC| 3.3V
GND| GND
VRx| GPIO 34
VRy| GPIO 35
SW| GPIO 27

«Note: GPIO 34 and GPIO 35 are input-only GPIOs on ESP32 and are suitable for reading the joystick analog outputs.»

🔌 Car Unit Connections

L298N| ESP32
ENA| GPIO 25
IN1| GPIO 26
IN2| GPIO 27
IN3| GPIO 32
IN4| GPIO 33
ENB| GPIO 14
GND| GND

Motor Configuration

- Left Front Motor → Left Motor Output
- Left Rear Motor → Left Motor Output
- Right Front Motor → Right Motor Output
- Right Rear Motor → Right Motor Output
- Motors on each side are connected in parallel.

🎮 Control System

Joystick Movement| Car Action
Push Forward| ⬆️ Move Forward
Push Backward| ⬇️ Move Backward
Move Left| ⬅️ Turn Left
Move Right| ➡️ Turn Right
Release / Center| 🛑 Stop
Press Joystick SW| 🛑 Stop

📡 Wireless Communication

The two ESP32 boards communicate using ESP-NOW.

Why ESP-NOW?

- No Wi-Fi router required
- Low-latency communication
- Fast response
- Suitable for robotics and remote-control applications
- ESP32-to-ESP32 direct communication

🔋 Power System

Car Unit

- Battery: 11.1V Li-ion battery
- Battery powers the L298N motor driver and motors.
- ESP32 should receive a suitable regulated supply.

Joystick Unit

The ESP32 can be powered using:

- 5V power bank, or
- Suitable Li-ion battery with a regulated 5V/3.3V supply.

⚠️ Important: Always ensure the ESP32 receives the correct regulated voltage.

🧠 How It Works

1. The user moves the joystick.
2. ESP32 reads the VRx and VRy analog values.
3. The joystick values are converted into movement commands.
4. The transmitter ESP32 sends the command using ESP-NOW.
5. The receiver ESP32 receives the command.
6. The receiver controls the L298N motor driver.
7. The L298N drives the four motors according to the received command.

🛠️ Technologies & Components

Hardware

- ESP32 × 2
- Arduino Joystick Module × 1
- L298N Motor Driver × 1
- DC Gear Motors × 4
- 11.1V Li-ion Battery
- Robot Car Chassis
- Jumper Wires

Software

- Arduino IDE
- ESP32 Arduino Core
- ESP-NOW
- C/C++

📁 Suggested Repository Structure

Wireless-Joystick-Controlled-4-Wheel-Robot-Car/
│
├── Joystick_Unit/
│   └── Joystick_Transmitter.ino
│
├── Car_Unit/
│   └── Car_Receiver.ino
│
├── Documentation/
│   └── ESP32_Joystick_Unit_Wiring_Diagram.pdf
│
├── Images/
│   └── wiring-diagram.png
│
└── README.md

🚀 Future Improvements

- Add obstacle detection using ultrasonic sensors
- Add speed control using PWM
- Add battery voltage monitoring
- Add emergency stop functionality
- Add OLED/LCD status display
- Improve joystick sensitivity and dead-zone control
- Add autonomous driving mode
- Add multiple robot control

🎯 Project Goal

The main goal of this project is to develop a low-latency wireless robotic vehicle using ESP32 and ESP-NOW while gaining practical experience in:

- Embedded systems
- IoT communication
- Wireless networking
- Motor control
- ESP32 programming
- Robotics
- Hardware interfacing

👨‍💻 Author

Saindu Wishshanka

GitHub: Sasidu-Tech

---

⭐ If you find this project useful, consider giving the repository a star!
