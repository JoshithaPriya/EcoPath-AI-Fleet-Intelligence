# 🚛 EcoPath  – Fleet Intelligence

##  Project Overview

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

##  How It Works (Short Flow)
generator.py → main.py → live_dashboard_data.csv → dashboard.py


---

## 1️ generator.py

Simulates live telemetry every 2 seconds:

- timestamp  
- vehicle_id  
- gps_speed_kmph  
- engine_status  
- j1939_fuel_rate_lph (nullable)

---

## 2️ main.py (Pathway Streaming)

Performs:

- Fuel estimation (if missing)
- Rate → Volume conversion
- CO₂ calculation

Output:
live_dashboard_data.csv


---

## 3️ dashboard.py (Streamlit)

Displays:

- Total Fleet  
- Active Trucks  
- Total CO₂ (kg)  
- Wasted Fuel (L)  

Map colors:
- 🔵 Normal
- 🔴 Idling

- <img width="1911" height="967" alt="image" src="https://github.com/user-attachments/assets/b9aebf9d-140b-429a-943a-19fcd7e502a0" />


<img width="1916" height="969" alt="image" src="https://github.com/user-attachments/assets/2c1f95a2-3a4e-42cc-9ee6-dde1997af025" />

