# T2601 — API Arduino
> Modular I/O expansion board based on the ATmega328P.

![ATmega328P](https://img.shields.io/badge/MCU-ATmega328P-blue)
![Arduino ISP](https://img.shields.io/badge/Prog-Arduino_ISP-green)
![UART Chain](https://img.shields.io/badge/Com-UART_Chain-purple)
![Open Hardware](https://img.shields.io/badge/License-CERN_OHL_v2-orange)

---

## System Architecture

### 🟦 Main Board
_Mother board of the system — orchestrates the entire bus_

- Hosts a compact dev board (Teensy-style)
- **3 Mezzanine slots** for I/O interface cards
- **N System Mezzanine slots** for advanced modules
  - FRAM / RTC / MicroSD / ... modules
- Power management for the entire system

---

### 🟩 Extension Board
_Bus slave node — based on the ATmega328P_

- Microcontroller: **ATmega328P**
- **2 Mezzanine slots** for I/O
- **Chained UART** communication across all extension boards
- Programming via **Arduino as ISP**

---

### 🟨 Mezzanine Card
_Hot-swappable I/O interface module — 25 × 25 mm_

| Driver         | Type        | Typical Use                  |
|----------------|-------------|------------------------------|
| ULN2803        | Sink NPN    | Relays, inductive loads      |
| MIC2981        | Source PNP  | High-voltage loads           |
| MOSFET         | Switch      | Power loads                  |
| Voltage divider| Passive     | Analog input                 |
| Optocoupler    | Isolated    | Galvanic isolation           |

---

## Repository Structure
```
T2601_APIArduino/
├── hardware/
│   ├── main_board/        # Main board
│   ├── extension_board/   # ATmega328P extension board
│   └── mezzanine/         # I/O mezzanine cards
├── firmware/              # Arduino code
├── docs/                  # Schematics, datasheets
└── README.md
```

---

## License

This project is open hardware — **CERN OHL v2 Permissive**.
