Digital Stethoscope with Multi-Sensor Health Monitoring

Overview

This project implements a Digital Stethoscope prototype using the ESP32-WROOM-32 development board.
It integrates multiple biomedical sensors to measure ECG, heart rate, SpO₂, body temperature, and stethoscope mic signals, displaying them in real-time on an OLED screen and the Arduino Serial Plotter.

This prototype validates the core system for future MVP development, where discrete modules will be integrated into a single compact PCB or custom IC.

Features

ECG Monitoring

Single-lead ECG using AD8232 sensor

Real-time waveform visualization on Serial Plotter

Centered and scaled output for clean PQRST waveform

Pulse Oximeter & Heart Rate (SpO₂ + HR)

Based on MAX30102 / MAX30105 sensor

Algorithm for accurate SpO₂ (%) and Heart Rate (bpm) calculation

Stable HR readings averaged per minute to reduce noise

Digital Microphone (Stethoscope mode)

Captures heart/lung sounds via electret/digital mic connected to ESP32 ADC

Displayed as waveform in Serial Plotter for analysis

Temperature Monitoring

MAX30205 precision body temperature sensor

Reads temperature in Celsius with ±0.1°C accuracy

OLED Display (SSD1306, 128×64)

Real-time updates of HR, SpO₂, and Temperature

Graphical icons for each parameter (HR, Temp, SpO₂)

Moving title animation for branding ("GEMINEX Health Care")

Communication & Debugging

Serial interface for waveform plotting and debugging

Future scope: BLE integration for wireless data streaming

System Architecture

ESP32-WROOM-32 MCU acts as the central controller:

Analog Inputs

ECG: GPIO32

MIC: GPIO33

I²C Bus (SDA=21, SCL=22)

MAX30102/MAX30105 (SpO₂ + HR)

MAX30205 (Temperature)

SSD1306 OLED Display

🔌 Hardware Used

ESP32-WROOM-32 Dev Board (30 pins)

AD8232 ECG Module + 3 ECG electrodes (Red, Yellow, Blue)

MAX30102/MAX30105 Pulse Oximeter sensor

MAX30205 Temperature sensor

Electret/Digital microphone module

SSD1306 128×64 OLED display (I²C)

Resistors: 220Ω, 1kΩ

Capacitors: 0.1µF (decoupling), others as required

USB Type-C / Micro-USB cable for programming + power

🛠️ Software

ESP_IDF

Libraries used:

Wire.h (I²C communication)

MAX30105.h + spo2_algorithm.h (SpO₂ & HR calculation)

Protocentral_MAX30205.h (temperature sensor)

Adafruit_GFX.h + Adafruit_SSD1306.h (OLED display)

📊 Output Data

OLED → HR (bpm), SpO₂ (%), Temperature (°C)

Serial Plotter →

🔵 ECG waveform

🟠 Microphone (heart/lung sounds) waveform

---How This Helps in MVP

Prototype verifies core functions (signal acquisition, processing, display)

Provides a working demo for client validation

MVP stage will focus on:

Miniaturization (custom PCB instead of modules)

Power optimization (battery management)

Wireless connectivity (BLE/WiFi)

Noise cancellation (borrowing ideas from ANC headsets for mic/ECG filtering)

--- Future Enhancements

Add multi-lead ECG support (3-lead)

Integrate BLE/WiFi data streaming to mobile/PC app

On-device AI-based anomaly detection

Noise reduction using digital filtering (FIR/IIR, adaptive filters, ANC concepts)

Rechargeable Li-ion battery with charging circuit

---- Pin Connections
Component	ESP32 Pin	Notes
ECG (AD8232)	GPIO32	Analog input (Lead output)
Microphone	GPIO33	Analog input
OLED (SSD1306)	SDA=21, SCL=22	I²C interface
MAX30102/30105	SDA=21, SCL=22	I²C shared bus
MAX30205 Temp	SDA=21, SCL=22	I²C shared bus
🧾 License

This project is developed as part of GEMINEX Health Care Prototype.
For internal testing, demonstration, and MVP preparation.
