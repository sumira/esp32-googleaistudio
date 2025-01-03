# ESP32-CAM Vision Analysis with Gemini API

This project uses the ESP32-CAM module to capture images, send them to Google's Gemini API for analysis, and receive descriptive insights about the captured images. It demonstrates image capture, WiFi connectivity, HTTP communication, and AI-powered image description.

---

## Features

- Captures images using the ESP32-CAM module.
- Converts the captured image to base64 encoding.
- Sends the image to Google's Gemini API for analysis.
- Retrieves a descriptive analysis of the image from the API.
- Outputs the analysis results to the Serial Monitor.

---

## Prerequisites

### Hardware Requirements

- **ESP32-CAM module**  
  A compact and versatile camera module based on the ESP32 microcontroller.
- **Power supply**  
  Provide sufficient power via an FTDI adapter or external power source.

### Software Requirements

- **Arduino IDE**  
  With ESP32 board support installed.
- **Libraries**  
  Install the following libraries via the Arduino Library Manager:
  - `esp_camera`
  - `WiFi`
  - `HTTPClient`
  - `ArduinoJson`

---

## Configuration

### WiFi Settings

Update the following variables in the code with your WiFi network credentials:
```cpp
const char* ssid = "Your_WiFi_SSID";
const char* password = "Your_WiFi_Password";
```

### Gemini API Configuration

Replace the placeholder API key in the code with your valid Gemini API key:
```cpp
const char* gemini_api_key = "<Your_API_Key>";
```
The Gemini API endpoint is dynamically created in the code:
```cpp
String gemini_endpoint = "https://generativelanguage.googleapis.com/v1/models/gemini-1.5-flash:generateContent?key=" + String(gemini_api_key);
```

---

## Setup Instructions

1. **Install the ESP32 Board Support**
   - In Arduino IDE, navigate to `File > Preferences`.
   - Add the following URL to the "Additional Board Manager URLs" field:  
     `https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json`
   - Go to `Tools > Board > Boards Manager` and search for "esp32."
   - Install the ESP32 package.

2. **Connect the ESP32-CAM**
   - Connect the ESP32-CAM to your computer using an FTDI adapter.
   - Ensure correct wiring for uploading the code:
     - IO0 to GND during upload.
     - Remove the connection after uploading.

3. **Upload the Code**
   - Open the Arduino IDE.
   - Select the correct board (`ESP32 Wrover Module`) and port.
   - Click `Upload` to upload the code to the ESP32-CAM.

4. **Run the Code**
   - Open the Serial Monitor.
   - Set the baud rate to `115200`.
   - View WiFi connection status and image analysis results.

---

## Code Workflow

1. **Initialization**
   - The ESP32-CAM initializes the camera module and connects to the specified WiFi network.

2. **Image Capture**
   - Captures an image using the camera.
   - Encodes the captured image in base64 format for API compatibility.

3. **Data Transmission**
   - Sends the base64-encoded image to the Gemini API with a descriptive request payload.

4. **Response Handling**
   - Processes the API response to extract the image description.
   - Outputs the description to the Serial Monitor.

5. **Loop**
   - Repeats the process every 5 seconds.

---

## Example Serial Monitor Output

```plaintext
Connecting to WiFi...
WiFi connected
ESP32-CAM Vision Analysis

--- Starting New Image Analysis ---
Image captured, analyzing...
Sending request to Gemini API...
HTTP Response code: 200
Analysis Result:
"The image contains a red car on a sunny street with a clear blue sky in the background."
Waiting 5 seconds before next capture...
```

---

## Troubleshooting

### WiFi Connection Issues
- Double-check the WiFi credentials.
- Ensure the WiFi network is operational and within range.

### Camera Initialization Fails
- Verify the GPIO connections for the ESP32-CAM.
- Check the power supply to ensure adequate voltage and current.

### API Errors
- Ensure the API key is valid and authorized.
- Confirm the endpoint URL is correct and accessible.

---

## Notes

- Ensure sufficient power is provided to the ESP32-CAM to avoid instability during operation.
- API key usage may be subject to usage limits; monitor your account's quota.

---

## License

This project is licensed under the MIT License. You are free to use, modify, and distribute this software in accordance with the license terms.

---

## Author

**Sumira Pathirana**  
Department of Software Engineering,  
Faculty of Computing,  
Sabaragamuwa University of Sri Lanka.
