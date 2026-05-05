# 🚛 J1939 Sniffer Pro — Python CAN Bus Analyzer with Auto PGN Decoding

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![python-can](https://img.shields.io/badge/python--can-4.0+-orange.svg)](https://github.com/hardbyte/python-can)
[![Protocol](https://img.shields.io/badge/Protocol-SAE%20J1939-green.svg)](https://www.sae.org/standards/content/j1939/)
[![License](https://img.shields.io/badge/License-MIT--like-lightgrey.svg)](#-license)

> **Stop staring at raw hex dumps.** A professional CAN Bus / J1939 sniffer
> that decodes 29-bit PGN IDs into engineering units — RPM, °C, km/h —
> in real time. Built with Python and Tkinter, runs on Windows, macOS, and
> Linux.

J1939 Sniffer Pro screenshot
<img width="1280" height="720" alt="封面" src="https://github.com/user-attachments/assets/48c185ff-dc9b-45ca-8268-5de241f6f255" />


---

## 🎯 Why this exists

Professional tools like **Vector CANalyzer ($3,000+)** are out of reach for
most teams. Open-source `python-can` is powerful but ships no GUI and no
J1939 decoding. This project bridges the gap:

- **Clean Tkinter GUI** with live message table
- **Auto PGN parsing** — `18F00400` becomes "EEC1 — Engine Speed"
- **Demo Mode** so you can learn the protocol without any hardware
- **Universal hardware support** via `python-can` (Vector, PCAN, Kvaser,
  SocketCAN, slcan)

Built by a senior automation engineer who got tired of the "Vector or nothing" choice.

---

## 📂 Open Source vs Pro

This repo contains the **Community Edition** — a working J1939 sniffer with
basic decoding, free for personal and educational use.

The **[J1939 Sniffer Pro](https://pokhts.gumroad.com)** version on Gumroad
adds the production features I use in real client work:

| Feature | Community (this repo) | **[Pro Edition ($59)](https://pokhts.gumroad.com)** |
|---|:---:|:---:|
| 29-bit PGN extraction | ✅ | ✅ |
| Demo Mode (no hardware needed) | ✅ Basic | ✅ Realistic value drift |
| Auto-decode common PGNs (RPM, speed, temp) | ⚠️ Limited | ✅ 50+ PGNs |
| **Engineering unit conversion** (RPM = bits × 0.125) | ❌ | ✅ |
| **DM1 Active Fault Code parsing** (SPN + FMI) | ❌ | ✅ |
| **PGN whitelist filter** | ❌ | ✅ |
| **CSV recording** with timestamps | ❌ | ✅ |
| **Dark industrial UI theme** | ❌ | ✅ |
| **Commercial license** for client work | ❌ | ✅ |
| **Email support** | ❌ | ✅ |

### 👉 [Get J1939 Sniffer Pro on Gumroad — $59](https://pokhts.gumroad.com)

Or save $47 with the **[Industrial Python Toolkit Bundle](https://pokhts.gumroad.com)**
($129) — includes J1939 + Modbus + MQTT + EtherNet/IP.

---

## 🚀 Quick Start (Community Edition)

```bash
# Clone
git clone https://github.com/PhilYeh1212/Python-CAN-Bus-J1939-Sniffer-GUI
cd Python-CAN-Bus-J1939-Sniffer-GUI

# Install
pip install python-can

# Run
python main.py
```

Click **Demo Mode** in the GUI to see simulated J1939 traffic immediately.
No hardware required.

---

## 🔧 Hardware Compatibility

This tool works with any CAN interface supported by
[`python-can`](https://python-can.readthedocs.io/), including:

- **Vector** (CANcaseXL, VN1610, etc.)
- **Peak-System** (PCAN-USB, PCAN-PCI)
- **Kvaser** (Leaf Light, USBcan Pro)
- **Linux SocketCAN** (USB-CAN adapters, embedded boards)
- **slcan** / generic serial CAN devices
- **IXXAT** USB-to-CAN

---

## 📖 J1939 Decoding Logic

The 29-bit Extended CAN ID is decoded as follows:

```python
def parse_j1939_id(can_id):
    """Extract priority, PGN, and source address from a 29-bit J1939 ID."""
    priority = (can_id >> 26) & 0x7        # 3 bits
    pgn      = (can_id >> 8)  & 0x3FFFF    # 18 bits
    sa       = can_id & 0xFF               # 8 bits
    return priority, pgn, sa
```

The Pro version takes this further with engineering-unit conversion per the
SAE J1939-71 spec — for example, Engine Speed (PGN 61444, SPN 190) is
encoded as 16-bit unsigned with a **0.125 RPM/bit** scaling factor.

---

## 📚 Related reading

- [**Stop decoding Hex manually. I built a Python J1939 Sniffer with a GUI**](https://dev.to/philyeh/stop-decoding-hex-manually-i-built-a-python-j1939-sniffer-with-a-gui-no-hardware-needed-1p8o)
  — my Dev.to article about the design decisions behind this tool

---

## 📥 Get the Pro version

The Community Edition is the demo of what's possible. The
**[Pro version](https://pokhts.gumroad.com)** is what I actually use in
client work — production-quality, batteries-included, commercial license.

| Product | Price | Link |
|---|---:|---|
| 🚛 **J1939 Sniffer Pro** (this tool, Pro edition) | $59 | [Buy](https://pokhts.gumroad.com) |
| ⚙️ **Modbus Logger Pro** | $49 | [Buy](https://pokhts.gumroad.com) |
| 📡 **MQTT Logger Pro** | $39 | [Buy](https://pokhts.gumroad.com) |
| 🏭 **EtherNet/IP Study Kit** | $29 | [Buy](https://pokhts.gumroad.com) |
| 🔒 **Private ChatGPT Stack** | $59 | [Buy](https://pokhts.gumroad.com) |
| 📦 **Industrial Python Toolkit Bundle** (4 tools, save $47) | **$129** | [Buy](https://pokhts.gumroad.com) |
| 📊 **CSV Dashboard** (free companion tool) | $0 | [Download](https://pokhts.gumroad.com) |

---

## 📫 About

**Phil Yeh** — Senior Automation Engineer based in Taiwan. I build Python
tools for industrial protocol work.

- 🛒 **Store:** [pokhts.gumroad.com](https://pokhts.gumroad.com)
- ✍️ **Blog:** [dev.to/philyeh](https://dev.to/philyeh)

---

## 📝 License

The Community Edition in this repository is free for personal and
educational use. For commercial use (client projects, internal company
tools, products you sell), please get the **[Pro Edition](https://pokhts.gumroad.com)**
which includes a proper commercial license.

If this tool helped you, **a ⭐ on the repo** means a lot to an indie
developer. Thanks!

---

<sub>**Keywords:** Python, CAN Bus, SAE J1939, PGN Decoder, ECU, OBD2,
Sniffer, GUI, Tkinter, Automation, Vector CANalyzer alternative,
Heavy-duty vehicle diagnostics</sub>
