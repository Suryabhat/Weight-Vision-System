# Weight-Vision-System

A Raspberry Pi-based system for capturing images and measuring weights using the HX711 load cell amplifier. The data is stored in an Excel file for analysis.

## 📸 Features

- Capture images using PiCamera2
- Measure weight using HX711 + Load Cell
- Save timestamped images and data
- Log all records into an Excel sheet (`weight_data.xlsx`)
- Spacebar to capture, `q` to quit

## 🧰 Requirements

- Raspberry Pi (with PiCamera2 support)
- Load Cell + HX711 Module
- Python 3
- Required Libraries:
  - `opencv-python`
  - `picamera2`
  - `RPi.GPIO`
  - `openpyxl`
  - `hx711` (custom or installed)

## 🔧 Setup

📦 Hardware Requirements
| Component                      | Description                          |
| ------------------------------ | ------------------------------------ |
| Raspberry Pi (4/3/Zero W)      | With 40-pin GPIO header              |
| PiCamera Module (v2 or HQ)     | For capturing arecanut images        |
| Load Cell (e.g., 1kg)          | For weight measurement               |
| HX711 Module                   | Load cell amplifier for Raspberry Pi |
| Breadboard & Jumper Wires      | For prototyping the connections      |
| USB Keyboard, Monitor (or SSH) | To operate and view the GUI          |
| Weight Calibration Object      | Known weight (e.g., 100g or 200g)    |

🔌 Wiring Diagram
| HX711 Pin | Raspberry Pi GPIO Pin |
| --------- | --------------------- |
| **VCC**   | 5V (Pin 2 or 4)       |
| **GND**   | GND (Pin 6)           |
| **DT**    | GPIO10 (Pin 19)       |
| **SCK**   | GPIO11 (Pin 23)       |

You can change the GPIO pins in the code if needed.

🧰 Software Requirements

🐍 Python Version

Make sure you are using Python 3.7+

📦 Required Libraries

Install all required libraries using:

sudo apt update

sudo apt install -y python3-pip python3-opencv python3-picamera2 python3-openpyxl

pip3 install RPi.GPIO

If using a custom hx711.py file (your own driver for HX711), place it in the same directory as the main script.

🧪 First-Time Setup Steps

1. Enable the Camera
On Raspberry Pi, run:

sudo raspi-config

Go to Interface Options > Camera > Enable

Reboot the Pi: sudo reboot

2. Test the PiCamera
Try this test script:

from picamera2 import Picamera2
picam2 = Picamera2()
picam2.start_preview()
picam2.capture_file("test.jpg")

If test.jpg is saved, your camera is working.

3. Calibrate the HX711
   
When running the script for the first time, it will prompt: Put known weight on the scale and then press Enter:

Place your known weight on the load cell (e.g., 100g)

Enter the value 100 and press Enter

This calculates the scale ratio used in all further measurements

Controls:

Press SPACEBAR to capture an image and measure weight

Press Q to quit the application

Captured images saved in Arecanut_images/

Data logged in weight_data.xlsx with:

Timestamp

Weight in grams

Image path

🧪 Example Output

Image captured and saved as image_3_20250615_181200.jpg
Timestamp: 2025-06-15 18:12:00, Weight: 12.45 grams

Notes

Place a known weight for calibration at the beginning

Calibrate carefully to ensure accuracy

📜 License

This project is licensed under the MIT License.

🤝 Contributing

Pull requests are welcome. For major changes, open an issue first.

© 2025 Surya Narayana Bhat

---

### 📄 `requirements.txt`

```txt
opencv-python
openpyxl
RPi.GPIO
