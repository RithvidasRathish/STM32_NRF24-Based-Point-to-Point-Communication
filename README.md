**nRF24L01 Point-to-Point Communication using STM32

This repository demonstrates node-to-node (point-to-point) wireless communication using the nRF24L01 2.4 GHz RF module with STM32 microcontrollers.
The project uses SPI-based communication, hardware CRC, and FIFO buffering provided by the nRF24L01 for reliable data transfer.

📡 Project Overview

TX Node: STM32 Blue Pill (STM32F103)

RX Node: STM32 Black Pill (STM32F4 series)

Wireless Module: nRF24L01

Communication Type: Point-to-Point (P2P)

Payload: "Hello World"

Interface: SPI

Debug Output: UART (115200 baud)

The transmitter sends data periodically, and the receiver detects incoming packets using the STATUS register and processes them in real time.

🧩 Features

nRF24L01 TX/RX mode configuration

5-byte address-based filtering

Fixed RF channel selection

Hardware CRC validation

RX FIFO-based payload buffering

STATUS register–based packet detection

UART output for received data

LED indication for TX/RX events

🛠 Hardware Used
Transmitter (TX)

STM32 Blue Pill (STM32F103)

nRF24L01 module

Receiver (RX)

STM32 Black Pill (STM32F4)

nRF24L01 module**
