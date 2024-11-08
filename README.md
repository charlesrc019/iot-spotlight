# LED Traffic Light Controller

## Overview

This app is a web-controlled traffic light simulation for a Raspberry Pi. By utilizing the Flask web framework and the RPi.GPIO library, the app enables remote control over three LEDs (Red, Yellow, Green) that simulate traffic light behavior. The app includes manual control over individual lights and an automated mode that cycles through them.

---

## Features

- **Automated Mode**: The traffic lights cycle through green, yellow, and red in a set sequence, simulating a real-world traffic light.
- **Manual Control**: Access routes to control individual lights (green, yellow, red) from a web interface.
- **Simple Web Interface**: Easily toggle between modes from a browser using Flask's templating to serve pages for each mode.

---

## Installation

1. **Install Dependencies**:
   - Ensure you have Python installed on your Raspberry Pi.
   - Install Flask and RPi.GPIO libraries:
     ```bash
     pip install flask RPi.GPIO
     ```

2. **Set Up GPIO**:
   - Connect the LEDs to the designated GPIO pins on the Raspberry Pi:
     - **Red LED**: GPIO 17
     - **Yellow LED**: GPIO 21
     - **Green LED**: GPIO 22

3. **Run the App**:
   - Execute the script from the terminal:
     ```bash
     sudo python3 traffic_light.py
     ```
   - Access the app in a web browser at `http://<your_pi_ip_address>:80`.

---

## Usage

- **Home Page (`/`)**: Starts the automatic traffic light sequence.
- **Green Light (`/green`)**: Displays only the green light.
- **Yellow Light (`/yellow`)**: Displays only the yellow light.
- **Red Light (`/red`)**: Displays only the red light.

Each manual route halts the automated sequence if it’s running, allowing individual light control.

---

## Code Structure

- **Libraries**: `RPi.GPIO` for GPIO control, `flask` for the web framework, and `threading` for managing the automated mode.
- **Routes**: Defined for each light and the auto mode, each serving a corresponding HTML template.
- **Functions**:
  - `clear()`: Turns off all LEDs.
  - `red()`, `yellow()`, `green()`: Activates the corresponding LED.
  - `auto()`: Runs the automatic sequence of green, yellow, and red in a continuous loop.

---

## Notes

- **Permissions**: Running on port 80 requires root privileges (`sudo`).
- **Safety**: Always clear and shut down GPIOs to avoid damage when the app is closed.

---

## Troubleshooting

- **GPIO Warnings**: If you receive GPIO warnings, ensure `GPIO.cleanup()` is called after use, or disable warnings in the code.
- **Port Access**: Ensure the Raspberry Pi firewall allows traffic on port 80 or change to a different port in the code if needed.
