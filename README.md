# IoT-Based Warehouse Temperature and Humidity Monitoring System

> 📦 **Note:** The main repository for this project is hosted at [this repository](https://github.com/tzucun/Pemantauan-Suhu-dan-Kelembapan-berbasis-IoT-ESP32-DHT22-dan-Bot-Telegram).

---

## 📌 Project Overview

This project implements a real-time temperature and humidity monitoring system for warehouse storage, using IoT technology. It is designed to help prevent damage to goods caused by poor environmental conditions.

---

## 🎯 Main Features

- **Real-Time Monitoring**  
  Monitors warehouse temperature and humidity levels using the **DHT22** sensor connected to an **ESP32** microcontroller.

- **Automated Actuators**  
  Automatically activates a **fan** and a **siren** (via relay) when:
  - Temperature reaches **≥ 35°C**
  - Humidity drops to **≤ 40%**  
  These actuators turn off automatically once conditions return to safe levels.

- **Early Warning System via Telegram**  
  Sends alerts to users through a **Telegram Bot** if temperature or humidity exceeds defined thresholds, indicating an unsafe condition in the warehouse.

- **User Interaction through Telegram**  
  Users can communicate with the Telegram Bot to:
  - Check current temperature and humidity
  - View the status of the warehouse conditions
  - Use commands such as `/cek_ambang` to query thresholds

- **Web Dashboard Integration**  
  Features a comprehensive web-based dashboard for enhanced monitoring and control capabilities:
  - **Real-time Data Visualization**: Interactive charts and graphs displaying temperature and humidity trends
  - **Remote Control Interface**: Web-based controls for managing actuators and system settings
  - **Historical Data Analysis**: View past sensor readings and system performance
  - **Responsive Design**: Accessible from desktop and mobile devices
  - **API Integration**: RESTful API endpoints for seamless data exchange

---

## 🌐 Web Dashboard

This project includes a dedicated web dashboard for comprehensive monitoring and control of the warehouse system.

> 🔗 **Dashboard Repository**: [Warehouse-Dashboard](https://github.com/ElloRabyndra/Warehouse-Dashboard)

### Dashboard Features
- **Real-time monitoring** with live charts and gauges
- **Historical data visualization** with interactive timelines
- **System status overview** with actuator controls
- **Responsive design** for mobile and desktop access
- **API-driven architecture** for seamless integration

### API Endpoints
The ESP32 system exposes several API endpoints for dashboard integration:
- `GET /api/ping` - Check connection status
- `GET /api/status` - Get current temperature, humidity, and actuator status
- `POST /api/command` - Send control commands to ESP32
- **CORS Support** enabled for cross-origin requests

---

## 🧪 Simulation with Wokwi

This project is simulated using [Wokwi](https://wokwi.com/), with some adaptations:

- **Red LED** represents the **fan**
- **White LED** represents the **siren**

### ⚙️ Connecting with Web Dashboard (Wokwi)
To connect the Wokwi simulation with the web dashboard, configure port forwarding in `wokwi.toml`:

```toml
[wokwi]
version = 1
firmware = '.pio\build\featheresp32\firmware.bin'
elf = '.pio\build\featheresp32\firmware.elf'

[[net.forward]]
from = "localhost:8180"
to = "target:80"
```

---

## 🛠️ Implementation Design

| Real Hardware Design | Wokwi Simulation Design |
|----------------------|-------------------------|
| ![Real Hardware Design](screenshot/desain_implementasi.jpg) | ![Wokwi Simulation Design](screenshot/desain_wokwi.png) |

---

## 📸 Scenario Demonstrations

### ✅ Normal Conditions

| Wokwi Simulation | Telegram Bot |
|------------------|--------------|
| ![Normal - Wokwi](screenshot/aman.png) | ![Normal - Telegram](screenshot/notif_realtime.png) |

---

### 🌡️ Temperature ≥ 35°C

| Wokwi Simulation | Telegram Bot |
|------------------|--------------|
| ![High Temp - Wokwi](screenshot/kritis.png) | ![High Temp - Telegram](screenshot/suhu_kritis.png) |

---

### 💧 Humidity ≤ 40%

| Wokwi Simulation | Telegram Bot |
|------------------|--------------|
| ![Low Humidity - Wokwi](screenshot/kritis.png) | ![Low Humidity - Telegram](screenshot/kelembaban_kritis.png) |

---

### 💬 Command `/cek_ambang`

 | Telegram Bot |
 |--------------|
 | ![Command cek_ambang - Telegram](screenshot/cek_ambang.png) |

---

## 🤖 Interacting with the Telegram Bot
The Telegram bot allows you to remotely monitor warehouse conditions and trigger commands.
> Telegram Bot Link: [@pemantauanGudangBot](https://t.me/PemantauanGudangBot).