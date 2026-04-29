# 🌡️ ESP32 Weather Station (Web Dashboard)

A simple ESP32-based weather station that reads temperature and humidity using a DHT11 sensor and displays the data on a live web dashboard.

The ESP32 hosts a web server with a modern UI and provides a JSON API for real-time data.

## 🚀 Features
📡 Wi-Fi enabled ESP32 web server
🌡️ Real-time temperature monitoring
💧 Humidity tracking
🌐 Live dashboard with auto-refresh (every 2 seconds)
🔌 REST API endpoint (/api)
⚡ Non-blocking sensor reading
🔁 Auto Wi-Fi reconnect
## 🛠️ Hardware Required
ESP32 Development Board
DHT11 Temperature & Humidity Sensor
Jumper wires
Breadboard (optional)
🔌 Circuit Diagram
DHT11 Pin	ESP32 Pin
VCC	3.3V
GND	GND
DATA	GPIO 18
## 📦 Libraries Used

Make sure you install the following libraries in Arduino IDE:

WiFi.h (built-in)
WebServer.h (built-in)
ESPmDNS.h (built-in)
DHT sensor library by Adafruit
## ⚙️ Setup Instructions
Clone this repository or copy the code
Open in Arduino IDE
Install required libraries
Update Wi-Fi credentials:
const char *ssid = "YOUR_WIFI_NAME";
const char *password = "YOUR_WIFI_PASSWORD";
Upload code to ESP32
Open Serial Monitor (115200 baud)
## 🌐 Accessing the Dashboard

After connecting, you'll see an IP in Serial Monitor like:

192.168.x.x

Open it in your browser:

http://<ESP32_IP>

OR (if mDNS works):

http://esp32.local
## 📡 API Endpoint

You can fetch sensor data in JSON format:

GET /api
## Example Response:
{
  "temperature": 28.5,
  "humidity": 65.2
}
### 💻 Web Dashboard
Clean glassmorphism UI
Auto updates every 2 seconds
Works on mobile & desktop
### 🔄 How It Works
ESP32 connects to Wi-Fi
DHT11 sensor reads temperature & humidity
Data is cached and updated every 2 seconds
Web server serves:
/ → Dashboard UI
/api → JSON data
Frontend fetches data using JavaScript
### ⚡ Code Highlights
Non-blocking Sensor Read
if (millis() - lastRead > interval) {
  lastRead = millis();
}
JSON API
server.on("/api", handleAPI);
Live Data Fetch (Frontend)
setInterval(fetchData, 2000);
## ⚠️ Notes
DHT11 is not very accurate; consider upgrading to DHT22
Ensure stable Wi-Fi for best performance
mDNS (esp32.local) may not work on all networks
## 🔮 Future Improvements
Add historical data logging
Display charts (temperature/humidity trends)
Add OTA updates
Support multiple sensors
Mobile app integration
## 📜 License

This project is open-source and free to use.
