# ESP32-Hand-gesture-car

# ESP32 Gesture Controlled Rover using ESP-NOW

A wireless gesture-controlled robotic car built using two ESP32 boards and an MPU-6500 motion sensor.  
The transmitter detects hand movement using the MPU sensor and sends commands wirelessly through ESP-NOW.  
The receiver ESP32 controls the motors of the rover accordingly.

---

## Features

- Wireless communication using ESP-NOW
- Gesture-based rover control
- Forward, Backward, Left, Right movement
- Real-time motion response
- Low latency communication
- No WiFi router required

---

## Hardware Used

### Transmitter Side
- ESP32
- MPU-6500 / MPU-6050
- Jumper wires
- Battery supply

### Receiver Side
- ESP32
- L298N Motor Driver
- DC Motors
- Chassis
- Battery pack

---

## Working Principle

1. MPU sensor detects hand tilt/movement.
2. ESP32 transmitter processes accelerometer data.
3. Command is generated:
   - `F` → Forward
   - `B` → Backward
   - `L` → Left
   - `R` → Right
   - `S` → Stop
4. Command is sent wirelessly using ESP-NOW.
5. Receiver ESP32 receives the command and drives motors.

---

# Transmitter Connections

| MPU6500 | ESP32 |
|--------|--------|
| VCC | 3.3V |
| GND | GND |
| SDA | GPIO 21 |
| SCL | GPIO 22 |

---

# Receiver Connections

## Motor Driver Pins

| L298N | ESP32 |
|------|--------|
| IN1 | GPIO 23 |
| IN2 | GPIO 22 |
| IN3 | GPIO 19 |
| IN4 | GPIO 18 |
| ENA | GPIO 25 |
| ENB | GPIO 26 |

---

## ESP-NOW Setup

Replace the receiver MAC address in transmitter code:

```cpp
uint8_t receiverMac[] = { 0x00, 0x4B, 0x12, 0x2F, 0x0C, 0x64 };
```

To find receiver MAC address:

```cpp
Serial.println(WiFi.macAddress());
```

Upload receiver code first and check Serial Monitor.

---

# Libraries Required

Install these libraries in Arduino IDE:

- WiFi.h
- esp_now.h
- Wire.h

---

# How to Run

## Step 1
Upload receiver code to rover ESP32.

## Step 2
Open Serial Monitor and copy MAC address.

## Step 3
Update transmitter code with receiver MAC.

## Step 4
Upload transmitter code.

## Step 5
Power both ESP32 boards.

## Step 6
Tilt transmitter to control rover.

---

# Gesture Controls

| Gesture | Action |
|---------|---------|
| Tilt Forward | Move Forward |
| Tilt Backward | Move Backward |
| Tilt Left | Turn Left |
| Tilt Right | Turn Right |
| Keep Flat | Stop |

---

# Project Structure

```bash
├── receiver.ino
├── transmitter.ino
└── README.md
```

---

# Future Improvements

- Add obstacle avoidance
- Add camera streaming
- Add speed control using PWM
- Add rechargeable battery system
- Add mobile app control

---

# Applications

- Robotics projects
- Gesture control systems
- Surveillance rover
- Educational IoT projects
- Wireless vehicle control

---

# Author

Sahil Sharma

---

# License

This project is open-source and free to use for educational purposes.
