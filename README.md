# Automated Rain Responsive Shutter and Protection Mechanism

<div align="center">

[![GitHub Repository](https://img.shields.io/badge/GitHub-Repository-00f0ff?style=for-the-badge&logo=github&logoColor=white)](https://github.com/ALWINTR/Automated-Rain-Responsive-Shutter-and-Protection-Mechanism)
[![Developer](https://img.shields.io/badge/Developer-Alwin_T_R-0284c7?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/alwintr)
[![Portfolio](https://img.shields.io/badge/Portfolio-alwintr.github.io-00f0ff?style=for-the-badge&logo=googlechrome&logoColor=black)](https://alwintr.github.io)
[![License](https://img.shields.io/badge/License-MIT-10b981?style=for-the-badge)](LICENSE)

</div>

> Automated weather-responsive protective shutter system utilizing FC-37 precipitation sensor, software hysteresis debounce filter, and precision SG90 servo angle actuation.

---

## 📌 Executive Overview

Automated weather-responsive protective shutter system utilizing FC-37 precipitation sensor, software hysteresis debounce filter, and precision SG90 servo angle actuation. This repository contains production-ready firmware implementations, hardware wiring pinouts, signal conditioning routines, and real-time telemetry pipelines engineered for reliable physical operation.

- **Primary Domain**: Industrial Automation
- **Microcontroller & Hardware Core**: Arduino / Servo
- **Specialization**: Weather Automation
- **Live Specs & BOM Viewer**: [alwintr.github.io](https://alwintr.github.io)

---

## 📐 System Architecture & Signal Flow

```
[ Precipitation / Raindrops ] ===> [ FC-37 Nickel Sensor Plate ]
                                             | Resistive Voltage Divider
                                             v
                                  [ LM393 Comparator Module ]
                                             | Analog Voltage & Digital Trigger
                                             v
+--------------------------------------------------------------+
|                     Arduino Uno ATmega328P                   |
|  - Moving Average Noise Filter - 1500ms Hysteresis Debounce  |
|  - State Machine: DRY -> PRECIPITATION_DETECTED -> SHUTTERED |
+--------------------------------------------------------------+
                                |
                                v Timer PWM Signal
                   +--------------------------+
                   |  TowerPro SG90 Servo     |
                   |  ==> Protective Cover    |
                   +--------------------------+
```

---

## 📋 Hardware Bill of Materials (BOM)

| Component Name | Operating Voltage | Interface / Functionality |
| :--- | :--- | :--- |
| **Arduino Uno R3** | `5V DC` | Main controller |
| **FC-37 Raindrop Board** | `3.3V - 5V` | Nickel-plated interdigitated sensing grid |
| **LM393 Comparator IC** | `5V DC` | Onboard trimmer for threshold sensitivity |
| **TowerPro SG90 Servo** | `5V DC` | Micro servo motor (1.8 kg-cm) |
| **Bicolor Status Indicator** | `5V DC` | Green (Open/Clear), Amber (Deploying), Red (Closed) |

---

## 🔌 Circuit Pinout & Microcontroller Interconnect

| MCU Pin / Channel | Peripheral Pin | Signal Function / Bus |
| :--- | :--- | :--- |
| `Arduino Analog Pin A0` | `LM393 Analog Out` | Precipitation Intensity ADC |
| `Arduino Digital Pin 2` | `LM393 Digital Out` | Hardware Comparator Interrupt |
| `Arduino Digital Pin 9` | `SG90 Servo Signal` | 16-Bit PWM Angle Driver |
| `Arduino Digital Pin 11, 12` | `Status LEDs` | Operating State Indicators |

---

## ⚙️ Firmware Architecture & Control Logic

Dual-threshold noise cancellation with rolling average window and 1500ms mechanical hysteresis debounce to prevent servo jitter during sporadic rainfall.

### Key Firmware Capabilities:
- **Zero-Blocking Architecture**: Real-time non-blocking scheduling eliminating delay() deadlocks.
- **Hardware Interrupt Servicing**: Microsecond-precision edge-triggered pulse detection and safety shutoffs.
- **Diagnostic Telemetry**: Continuous serial datastreaming and state-machine transition logging.

---

## 📁 Repository Structure

```
Automated-Rain-Responsive-Shutter-and-Protection-Mechanism/
├── .gitignore
├── LICENSE
├── rain_sensor_servo.ino
└── README.md
```

---

## 🚀 Build & Deployment Instructions

### 1. Hardware Assembly
- Verify common system ground across all microcontrollers, drivers, and peripheral sensor boards.
- Ensure dedicated power supply rails match the operating voltage specified in the Hardware Bill of Materials.

### 2. Firmware Compilation & Flashing
```bash
# Clone the repository
git clone https://github.com/ALWINTR/Automated-Rain-Responsive-Shutter-and-Protection-Mechanism.git

# Navigate to the project directory
cd Automated-Rain-Responsive-Shutter-and-Protection-Mechanism
```

- Open the project in **Arduino IDE**, **PlatformIO**, or **ESP-IDF**.
- Select the target board configuration and COM port.
- Compile and upload firmware directly to the microcontroller.

---

## 👨‍💻 Author

**Alwin T R** — Robotics & Automation Engineer  
- 💼 **LinkedIn**: [linkedin.com/in/alwintr](https://www.linkedin.com/in/alwintr)  
- 🌐 **Interactive Portfolio**: [alwintr.github.io](https://alwintr.github.io)  
- 🐙 **GitHub**: [github.com/ALWINTR](https://github.com/ALWINTR)  
- ✉️ **Direct Email**: [alwintr2003@gmail.com](mailto:alwintr2003@gmail.com)

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.
