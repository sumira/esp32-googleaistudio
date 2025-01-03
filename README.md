# ESP32-CAM Vision Analysis with Gemini API

This project demonstrates how to use an ESP32-CAM module to capture images, send them to the Gemini API for analysis, and receive descriptive insights. It combines image capture, WiFi connectivity, and HTTP communication with Google's Gemini AI for image content description.

---

## Features

- Captures images using the ESP32-CAM module.
- Sends the captured images to the Gemini API for analysis.
- Processes and outputs descriptive insights about the image.
- Uses base64 encoding to handle image data.

---

## Prerequisites

### Hardware
- ESP32-CAM module.
- Power source for ESP32-CAM (e.g., FTDI adapter or external power supply).

### Software
- Arduino IDE with ESP32 board support.
- WiFi network for ESP32-CAM to connect.
- Gemini API key for accessing Google's AI services.

---

## Code Overview

### Dependencies
The code includes the following libraries:
- `esp_camera.h`: For camera control.
- `WiFi.h`: For WiFi connectivity.
- `HTTPClient.h`: For making HTTP requests.
- `ArduinoJson.h`: For creating and parsing JSON.

### Key Configurations
#### WiFi Settings
```cpp
const char* ssid = "Your_SSID";
const char* password = "Your_Password";
