# nRF24L01 Point-to-Point Communication using STM32

This project demonstrates **reliable point-to-point (P2P) wireless communication** using the **nRF24L01 2.4 GHz transceiver** with **STM32 microcontrollers**.  
It focuses on **register-level operation**, **STATUS flag handling**, and **address + channel configuration** for robust packet-based communication.

---

## 📌 Project Summary

- **TX Node:** STM32 Blue Pill (STM32F103)
- **RX Node:** STM32 Black Pill (STM32F4 series)
- **Wireless Module:** nRF24L01
- **Protocol:** Proprietary 2.4 GHz (ShockBurst™)
- **Payload Size:** Up to 32 bytes
- **Interface:** SPI
- **Debug Interface:** UART (115200 baud)

The transmitter periodically sends data, while the receiver detects incoming packets using the **STATUS register (RX_DR flag)** and processes them in real time.

---

## ✨ Key Features

- Point-to-point wireless communication
- 5-byte address-based packet filtering
- Fixed RF channel configuration
- Hardware CRC verification
- RX FIFO buffering (up to 3 payloads)
- STATUS register–based packet detection
- UART output for received payload
- LED indication for TX/RX activity

---

## 🛠 Hardware Requirements

### Transmitter (TX)
- STM32 Blue Pill (STM32F103)
- nRF24L01 module

### Receiver (RX)
- STM32 Black Pill (STM32F4)
- nRF24L01 module

⚠️ **Important:**  
nRF24L01 operates at **3.3 V only**. Do NOT connect to 5 V.

---

## 📶 Address and Channel Configuration

- **Address Width:** 5 bytes
- EE DD CC BB AA
- Same address configured on both TX and RX
- Communication occurs on a **fixed RF channel** (0–125 range) -  CHANNEL 10 
- Only packets matching **both address and channel** are accepted

This combination provides logical separation between different wireless links.

---

## 🧠 Packet Reception Mechanism (STATUS Register)

The nRF24L01 uses the **STATUS register (0x07)** to signal events.

### RX Flow:
1. Packet arrives on the configured address and channel
2. nRF24L01 performs **hardware CRC check**
3. Payload is pushed into the **RX FIFO**
4. **RX_DR (Data Ready)** bit is set in STATUS
5. MCU polls STATUS using `isDataAvailable()`
6. Payload is read using `R_RX_PAYLOAD`
7. RX_DR flag is cleared by writing `1` to STATUS

This ensures efficient packet handling with minimal MCU overhead.

---

## 💻 Software Stack

- STM32 HAL drivers
- SPI-based nRF24L01 driver
- Polling-based RX 
- UART for debugging and data logging

---



