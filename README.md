> **🔥 BLACK FRIDAY SALE:** Get **15% OFF** all source codes with code `BLACKFRIDAY`. [**Click here to apply discount automatically**](https://pokhts.gumroad.com/l/senior-engineer-toolkit?offer_code=BLACKFRIDAY)



# 🚛 Python CAN Bus & J1939 Sniffer (GUI Source Code)

[![Python](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![Library](https://img.shields.io/badge/python--can-4.0+-orange.svg)]()
[![Protocol](https://img.shields.io/badge/Protocol-SAE%20J1939-green.svg)]()

> **Stop struggling with raw Hex dumps.**
> A production-ready CAN Bus Sniffer that **automatically decodes J1939 PGNs** (e.g., Engine Speed, Oil Temp) into human-readable text. Built with Python & Tkinter.

[J1939 Sniffer Demo]<img width="993" height="798" alt="螢幕擷取畫面 2025-11-19 161241" src="https://github.com/user-attachments/assets/9920ee28-86f9-40bb-8ce8-1e36e573cb60" />

---

## 🚀 Why this tool?
Professional tools like Vector CANalyzer are expensive. Simple Python scripts often lack a GUI.

This project bridges the gap. It provides a **Clean GUI** that connects to your hardware (Vector, PCAN, Kvaser, SocketCAN) and translates 29-bit J1939 IDs instantly.

**Perfect for:**
* 🚛 **Automotive Engineers:** Debugging Truck/Bus ECUs.
* 🤖 **Robotics Developers:** Monitoring CAN-based actuators.
* 🎓 **Students/Researchers:** Learning the J1939 protocol structure.

---

## ✨ Features
* **🚛 Native J1939 Parsing:** Automatically parses Priority, PGN, and Source Address.
    * *Example:* `18F00400` → **EEC1 - Engine Speed (RPM)**
* **🎮 Built-in Simulation:** No hardware? No problem. The **"Demo Mode"** generates realistic traffic so you can test the UI logic immediately.
* **🔌 Universal Support:** Works with any interface supported by `python-can` (slcan, socketcan, vector, pcan, ixxat, etc.).
* **📊 Live Monitor:** Real-time scrolling table with Timestamp, DLC, and Hex Data view.

## 🛠️ Dependencies
```bash
pip install python-can
```
📥 Download Full Source Code
Get the complete, fully commented source code (main.py). You can use it as a standalone tool or integrate the J1939 parsing logic into your own projects.

👉 Download on Gumroad ($9.9): [Link](https://pokhts.gumroad.com/l/python-can-j1939-tool)

(Includes: main.py, requirements.txt, and Setup Guide)

📖 Code Sneak Peek (J1939 Logic)
The code includes a helper function to extract PGNs from 29-bit Extended IDs:
```
Python

def parse_j1939_id(self, can_id):
    """Extract PGN and Source Address from 29-bit ID"""
    pgn = (can_id >> 8) & 0x3FFFF
    sa = can_id & 0xFF
    priority = (can_id >> 26) & 0x7
    return pgn, sa, priority
```
👨‍💻 About the Author
Phil Yeh - Senior Automation Engineer

My Gumroad Store ([More Engineering Tools](https://gumroad.com/products))

Keywords: Python, CAN Bus, J1939, SAE J1939, PGN Decoder, ECU, OBD2, Sniffer, GUI, Tkinter, Automation, Vector, PCAN
