# 📊 ATmega328P Data Logger with EEPROM and RTC

A low-power microcontroller-based data logger built using the ATmega328P.
It logs sensor data to a 512KB external EEPROM with timestamping provided by a real-time clock (RTC) module.
Ideal for offline data collection in environmental monitoring, industrial applications, or DIY electronics.

---

## 🔧 Features

- ✅ **Microcontroller:** ATmega328P @ 16 MHz
- 📦 **Memory:** 512KB External I2C EEPROM (e.g., 24LC512 or similar)
- 🕒 **Timekeeping:** DS3231 or DS1307 RTC module
- 📝 **Data Logging:** Logs data with accurate timestamps
- 🔌 **Interfaces:** I2C for EEPROM and RTC, UART for debugging
- 💾 **Power-Efficient:** Sleep modes enabled for long-term operation
- 🔄 **Circular/Sequential EEPROM writing** (selectable)
- 📠 **Data Dump via UART** on command

---

## 🛠️ Hardware Used

| Component         | Description                  |
|------------------|------------------------------|
| ATmega328P       | 8-bit AVR microcontroller     |
| 512KB EEPROM     | External I2C memory (e.g., 24LC512) |
| RTC Module       | DS3231 (preferred) or DS1307  |
| Crystal          | 16 MHz (if using bare MCU)    |
| Capacitors       | 22pF for crystal, 100nF decoupling |
| Resistors        | Pull-ups for I2C (4.7k–10kΩ)   |
| UART Header      | For serial debugging/data dump |
| Power Supply     | 5V regulated or battery with LDO |

---

## 🧑‍💻 Firmware Features

- Written in **C** using **AVR-GCC** and **AVR Libc**
- I2C master communication implemented for RTC and EEPROM
- UART command interface for:
  - Sending `LOG` to start logging
  - Sending `DUMP` to print stored data
  - Sending `CLR` to clear memory
- EEPROM wear-leveling (optional)
- Time and date initialization via UART or precompiled settings

---

## 📂 Folder Structure

```bash
.
├── src/
│   ├── main.c
│   ├── rtc.c / rtc.h
│   ├── eeprom.c / eeprom.h
│   ├── uart.c / uart.h
│   └── utils.c / utils.h
├── include/
├── Makefile
├── README.md
└── schematics/
    └── datalogger_schematic.pdf
