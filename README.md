Smart Solar Tracking System (IoT)An ESP32-based single-axis solar tracker that automatically orients a solar panel toward the strongest light source to maximize energy harvesting. The system integrates with the Blynk IoT platform for real-time monitoring of power output and environmental conditions.

🚀 Features

1. Active Tracking: Uses dual LDRs to compare light intensity and adjust the servo motor angle in real-time.
2. IoT Dashboard: Remote monitoring of voltage, temperature, and sun position via the Blynk app.
3. Environmental Intelligence: Built-in logic to determine weather conditions (e.g., "Sunny and Hot", "Cloudy and Mild").
4. Fail-safe Connectivity: Auto-reconnect logic for both Wi-Fi and Blynk services.

🛠️ Hardware ComponentsMicrocontroller:

* ESP32 (NodeMCU)
*  Actuator: MG995 or SG90 Servo Motor
*  Sensors:
  * 2x LDR (Light Dependent Resistors)
  * LM35 Temperature Sensor
  * Voltage Sensor Module (0-25V)
* Power: Solar Panel (size dependent on your motor/voltage divider)

📌 Pin Mapping

ComponentESP32 PinDescription
* LDR 1- GPIO 34Left/Top 
* LDR 2- GPIO 35Right/Bottom 
* LM35- GPIO 32
* Voltage Sensor- GPIO 33
* Servo Motor- GPIO 13

💻 Software Requirements

The following libraries are required to compile the code:
* WiFi.h (Built-in)
* BlynkSimpleEsp32.h
* ESP32Servo.h

⚙️ Setup InstructionsBlynk Setup:

Create a new template in the Blynk Console and add Virtual Pins: 
* V0, V1: LDR Values
* V2: Temperature (°C)
* V3: Voltage (V)
* V4: Servo Angle
* V5: Weather Condition (String)
* Configuration: Update the BLYNK_AUTH_TOKEN, ssid, and pass variables in the code with your credentials.
* Calibration: Adjust the ldrThreshold and angleStep constants in the code to fine-tune the sensitivity of the movement.
  
📊 Logic FlowSensing:
1. The system reads analog values from two LDRs.
2. Comparison: It calculates the difference (ldrDiff) between the two sensors
3. .Adjustment: If the difference exceeds the threshold, the servo increments/decrements its position to equalize the light levels.
4. Reporting: Data is pushed to the Blynk Cloud every 2000ms.
