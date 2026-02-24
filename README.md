🚛 EcoPath AI

Real-Time Fleet Telemetry & CO₂ Monitoring Pipeline

🔹 Project Overview

EcoPath AI is a real-time streaming system that monitors a hybrid fleet of 4 trucks.

Modern trucks → Send J1939 fuel rate data

Legacy trucks → GPS-only, fuel estimated using physics

The system:

Standardizes fuel data

Calculates actual fuel consumption

Computes CO₂ emissions

Detects idling fuel waste

Displays everything live on a dashboard

Built using Pathway (streaming engine) + Streamlit (dashboard) and deployed via Google Colab + Ngrok.
🏗 How It Works (Short Flow)
generator.py → main.py (Pathway) → live_dashboard_data.csv → dashboard.py
1️⃣ generator.py

Simulates live telemetry every 2 seconds:

timestamp

vehicle_id

gps_speed_kmph

engine_status

j1939_fuel_rate_lph (nullable)

2️⃣ main.py (Pathway Streaming)

Performs:

Fuel Estimation (if missing)

1.5 + (speed × 0.08)

Rate → Volume Conversion

fuel_rate × (2 / 3600)

CO₂ Calculation

fuel_volume × 2.68

Outputs processed data to:

live_dashboard_data.csv
3️⃣ dashboard.py (Streamlit UI)

Displays:

Total Fleet

Active Trucks

Total CO₂ (kg)

Wasted Fuel (L)

🗺 Map:

🔵 Normal

🔴 Idling (Speed = 0 but fuel burning)

🚀 How to Run (Local)
1️⃣ Install dependencies
pip install pathway streamlit pydeck pandas pyngrok
2️⃣ Start telemetry generator
python generator.py
3️⃣ Start streaming engine
python main.py
4️⃣ Start dashboard
streamlit run dashboard.py
☁️ How to Run in Google Colab
Step 1 — Install packages
!pip install pathway streamlit pydeck pandas pyngrok
Step 2 — Start generator (background)
!python generator.py &
Step 3 — Start Pathway
!python main.py &
Step 4 — Expose Streamlit via Ngrok
from pyngrok import ngrok

ngrok.set_auth_token("YOUR_NGROK_TOKEN")

public_url = ngrok.connect(8501)
print(public_url)

Then run:

!streamlit run dashboard.py &

Open the Ngrok URL to access your dashboard.

🛠 Tech Stack

Python

Pathway

Streamlit

PyDeck

Ngrok

Google Colab
