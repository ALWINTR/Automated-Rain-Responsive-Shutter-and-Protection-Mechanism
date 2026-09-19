# Automated Rain Responsive Shutter and Protection Mechanism

[![GitHub Repository](https://img.shields.io/badge/GitHub-Repository-00f0ff?style=for-the-badge&logo=github&logoColor=white)](https://github.com/ALWINTR/Automated-Rain-Responsive-Shutter-and-Protection-Mechanism)
[![Developer](https://img.shields.io/badge/Developer-Alwin_T_R-0284c7?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/alwintr)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

An automated weather protection system that detects precipitation in real time, executes a software hysteresis debounce state machine, and deploys a servo-actuated protective shutter to shield outdoor electronic equipment from moisture and water ingress.

---

## System Architecture and Sensing Principle

The rain-responsive mechanism operates with zero-lag response:
1. **Precipitation Sensing**: The **FC-37 nickel sensor plate** detects raindrops bridging the conductive traces, lowering electrical resistance.
2. **Comparator Signal Conditioning**: The onboard **LM393 dual comparator** produces an analog intensity voltage (A0) and a digital trip signal (D0).
3. **Anti-Oscillation Hysteresis**: Firmware prevents mechanical fluttering caused by solitary raindrops or drying moisture.
4. **Precision Servo Actuation**: Deploys the protective shutter to 180 degrees upon rain confirmation, retracting to 0 degrees after a verified dry period.

---

## Hardware Bill of Materials (BOM)

| Component | Technical Specification | Functional Role |
| :--- | :--- | :--- |
| **Microcontroller** | Arduino Uno / Nano (ATmega328P) | Sensor polling and PWM pulse timing |
| **Rain Sensor Plate** | FC-37 Nickel-Coated PCB Grid | High-sensitivity moisture conductivity |
| **Comparator Module** | LM393 Dual Differential Comparator | Onboard sensitivity trimmer and threshold |
| **Actuator** | TowerPro SG90 9g Micro Servo | Mechanical protective cover deployment |
| **Status LEDs** | Blue (Rain Active) / Green (Standby) | Visual operational status feedback |

---

## Circuit Pinout Table

| Module Pin | Arduino Pin | Signal Type | Description |
| :--- | :--- | :--- | :--- |
| **FC-37 Analog (A0)** | Analog Pin A0 | Analog In (0-5V) | Moisture intensity (1023=Dry, <400=Heavy Rain) |
| **FC-37 Digital (D0)** | Digital Pin D2 | Digital In | Instant hardware threshold interrupt |
| **SG90 Servo Signal** | Digital Pin D9 | PWM Output (50Hz) | 0 degree (Retracted) to 180 degree (Protected) |
| **Blue Rain LED** | Digital Pin D7 | Digital Output | Active when precipitation is present |
| **Green Standby LED** | Digital Pin D8 | Digital Output | Active in dry resting state |

---

## Author

**Alwin T R** - Robotics and Automation Engineer  
- LinkedIn: [linkedin.com/in/alwintr](https://www.linkedin.com/in/alwintr)  
- Portfolio: [alwintr.github.io](https://alwintr.github.io)  
- GitHub: [github.com/ALWINTR](https://github.com/ALWINTR)

---

## License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.
