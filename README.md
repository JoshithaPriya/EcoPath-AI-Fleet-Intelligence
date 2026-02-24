# 🚛 EcoPath AI – Fleet Intelligence

## 🔹 Project Overview

EcoPath AI is a real-time fleet telemetry pipeline.

- Modern trucks → Send J1939 fuel rate
- Legacy trucks → GPS-only, fuel estimated using physics

The system:

- Standardizes fuel data  
- Calculates actual fuel consumption  
- Computes CO₂ emissions  
- Detects idling fuel waste  
- Displays everything live on a dashboard  

Built using **Pathway (streaming engine)** + **Streamlit (dashboard)**  
Deployed via **Google Colab + Ngrok**

---

## 🔄 How It Works (Short Flow)
generator.py → main.py → live_dashboard_data.csv → dashboard.py


---

## 1️⃣ generator.py

Simulates live telemetry every 2 seconds:

- timestamp  
- vehicle_id  
- gps_speed_kmph  
- engine_status  
- j1939_fuel_rate_lph (nullable)

---

## 2️⃣ main.py (Pathway Streaming)

Performs:

- Fuel estimation (if missing)
- Rate → Volume conversion
- CO₂ calculation

Output:
live_dashboard_data.csv


---

## 3️⃣ dashboard.py (Streamlit)

Displays:

- Total Fleet  
- Active Trucks  
- Total CO₂ (kg)  
- Wasted Fuel (L)  

Map colors:
- 🔵 Normal
- 🔴 Idling
