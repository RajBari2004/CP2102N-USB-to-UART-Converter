# CP2102N USB-to-UART Converter

<p align="center">
  <b>USB Type-C to UART Interface | CP2102N | Custom PCB | KiCad 9.0</b>
</p>

<p align="center">
  <img src="Images/pcb_3d_front.png" width="650">
</p>

## 📌 Project Overview

This project is a **custom USB-to-UART converter PCB** designed around the **Silicon Labs CP2102N USB-to-UART bridge controller**.

The board provides a reliable interface between a **USB Type-C host** and external UART-based embedded systems. It is intended for applications such as **microcontroller programming, firmware development, serial debugging, hardware testing, and embedded-system communication**.

The complete hardware design, including the schematic and PCB layout, was developed using **KiCad 9.0**.

---

## ✨ Key Features

* 🔌 USB Type-C input interface
* 🔄 CP2102N USB-to-UART bridge
* 🛡️ USB D+/D− ESD protection
* ⚡ USB-C CC configuration resistors
* 💡 TX/RX activity indication LEDs
* 🔄 Hardware reset interface
* 🔋 Local power-supply decoupling
* 📡 External UART interface header
* 🧩 Compact custom PCB layout
* 🛠️ KiCad 9.0 schematic and PCB design
* 📦 Manufacturing-ready design workflow

---

## 🏗️ System Architecture

```text
                USB TYPE-C
                    │
             ┌──────┴──────┐
             │ USB D+ / D− │
             │ ESD Protect │
             └──────┬──────┘
                    │
                    ▼
              ┌───────────┐
              │  CP2102N  │
              │ USB → UART│
              └─────┬─────┘
                    │
              ┌─────┴─────┐
              │           │
             TX/RX       RST
              │           │
              ▼           ▼
        ┌────────────────────┐
        │   External UART    │
        │       Header       │
        └────────────────────┘
```

---

## 🔌 USB Type-C Interface

The USB interface is implemented using a **USB Type-C receptacle**.

The design includes:

* USB VBUS
* USB D+
* USB D−
* GND
* CC1 / CC2 configuration resistors
* USB ESD protection

The CC pins use **5.1 kΩ pull-down resistors** to configure the board as a USB sink/device.

The USB data lines are protected against electrostatic discharge before reaching the USB-to-UART controller.

---

## 🔄 CP2102N USB-to-UART Bridge

The core of the design is the **CP2102N USB-to-UART bridge controller**.

It performs the conversion between:

```text
USB
 │
 ▼
CP2102N
 │
 ▼
UART
```

This allows a computer to communicate with an external microcontroller or UART-based embedded system through a standard USB connection.

### UART Signals

| Signal | Function       |
| ------ | -------------- |
| TX     | UART Transmit  |
| RX     | UART Receive   |
| RST    | Hardware Reset |
| VBUS   | Supply         |
| GND    | Ground         |

---

## 💡 TX/RX Activity Indicators

Dedicated LEDs are included to provide visual indication of UART communication activity.

```text
CP2102N TX ──► TX LED
CP2102N RX ──► RX LED
```

This makes debugging and serial communication monitoring easier during hardware development.

---

## 🔋 Power & Decoupling

The design includes local bypass/decoupling capacitors around the CP2102N and USB supply.

The decoupling network helps reduce supply noise and provides transient current locally to the IC.

The design includes multiple **100 nF ceramic capacitors** for high-frequency supply decoupling.

---

## 🛡️ USB ESD Protection

ESD protection is implemented on the USB data interface to improve robustness against electrostatic discharge entering through the USB connector.

```text
USB-C
  │
  ├── D+ ──► ESD Protection ──► CP2102N
  │
  └── D− ──► ESD Protection ──► CP2102N
```

This provides an additional protection layer between the external USB connector and the USB interface circuitry.

---

## 📐 PCB Design

The PCB was designed using **KiCad 9.0 PCB Editor**.

The layout focuses on:

* Compact component placement
* Short USB data connections
* Practical routing
* Power decoupling
* Clear connector placement
* Accessible UART header
* Manufacturing-oriented PCB layout

### PCB Layout

<p align="center">
  <img src="Images/pcb_layout.png" width="850">
</p>

### 3D Front View

<p align="center">
  <img src="Images/pcb_3d_front.png" width="700">
</p>

### 3D Back View

<p align="center">
  <img src="Images/pcb_3d_back.png" width="700">
</p>

---

## 📋 External UART Header

The board provides a dedicated **5-pin external interface**.

| Pin | Signal | Description   |
| --: | ------ | ------------- |
|   1 | GND    | Ground        |
|   2 | VBUS   | USB supply    |
|   3 | RX     | UART Receive  |
|   4 | TX     | UART Transmit |
|   5 | RST    | Reset         |

This header can be connected to external embedded platforms for development and debugging.

---

## 🧩 Hardware Components

| Component             | Function                  |
| --------------------- | ------------------------- |
| CP2102N               | USB-to-UART conversion    |
| USB Type-C Receptacle | USB connectivity          |
| ESD Protection        | USB data-line protection  |
| 5.1 kΩ Resistors      | USB-C CC configuration    |
| LEDs                  | TX/RX activity indication |
| Capacitors            | Supply decoupling         |
| UART Header           | External serial interface |

---

## 🛠️ Design Tools

| Tool                       | Purpose                |
| -------------------------- | ---------------------- |
| **KiCad 9.0**              | Schematic & PCB design |
| **KiCad Schematic Editor** | Circuit design         |
| **KiCad PCB Editor**       | PCB layout             |
| **KiCad 3D Viewer**        | PCB visualization      |

---

## 📁 Repository Structure

```text
CP2102N-USB-to-UART-Converter/
│
├── KiCad/
│   ├── USB To UART.kicad_pro
│   ├── USB To UART.kicad_sch
│   └── USB To UART.kicad_pcb
│
├── Images/
│   ├── schematic.png
│   ├── pcb_layout.png
│   ├── pcb_3d_front.png
│   └── pcb_3d_back.png
│
├── Gerber/
│   └── Manufacturing files
│
└── README.md
```

---

## 📷 Schematic

<p align="center">
  <img src="Images/schematic.png" width="1100">
</p>

---

## 🎯 Applications

This converter can be used for:

* Microcontroller programming
* UART debugging
* Embedded firmware development
* Serial communication
* ESP8266 / ESP32 development
* Arduino development
* Bootloader interfaces
* Hardware testing
* Development-board debugging
* General USB-to-UART communication

---

## 🧠 Engineering Concepts Demonstrated

This project demonstrates practical experience with:

* USB Type-C interface design
* USB 2.0 D+/D− routing
* USB ESD protection
* USB-C CC configuration
* USB-to-UART conversion
* UART interface design
* Power-supply decoupling
* Indicator LED circuits
* Connector interfacing
* Schematic capture
* PCB component placement
* PCB routing
* Footprint selection
* PCB design verification
* KiCad 9.0 workflow

---

## 🚀 Future Improvements

Possible future revisions could include:

* USB-C overvoltage/overcurrent protection
* Improved ESD protection
* Configurable UART voltage levels
* Additional UART control signals
* Test points for critical signals
* Mounting holes
* Status/power indicator
* Improved high-speed USB layout optimization
* Production-oriented DFM review

---

## 📌 Project Status

**Status:** Hardware Design Completed

**Design Stage:** Schematic + PCB Layout

**EDA Tool:** KiCad 9.0

**Interface:** USB Type-C → UART

**USB-to-UART IC:** CP2102N

---

## 👨‍💻 Author

**Raj.B**

B.Tech — Electronics & Telecommunication Engineering

Interested in **Embedded Systems, PCB Design, Hardware Development, IoT, and Power Electronics**.

---

## 📄 License

This project is provided for educational, development, and portfolio purposes.

If you use or modify this design, please provide appropriate attribution to the original project.
