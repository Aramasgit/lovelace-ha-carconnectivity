# lovelace-ha-carconnectivity
🚗 Carconnectivity Dashboard for Home Assistant

A modern and elegant Home Assistant dashboard to monitor and control your CarConnectivity compatible car.

## Preview 📸

<p align="center">
  <img width="1087" height="618" alt="heating" src="https://github.com/user-attachments/assets/7d59a18c-4c06-4ae3-8e6e-f0ab93aa2b4e" />
</p>


---

### 1. Features ✨

🔋 Dynamic gauges - Battery and fuel with adaptive colors

🌡️ Smart climate control - Shows Heating/Cooling/Ventilation based on temperature

⚡ Charging management - Control socket and vehicle charging

🎚️ Amperage selection - Buttons for 5A, 10A, 13A, 16A

📊 24h history - Battery and fuel graph

🖼️ Dynamic images - 7 different visual states for your vehicle

---

### 2. Requirements 📋

**Docker** to run:
- [CarConnectivity-MQTT](https://github.com/tillsteinbach/CarConnectivity)
- MQTT Broker (I use Mosquitto)

**HACS** integrations ([hacs.xyz](https://www.hacs.xyz/)):
- button-card
- stack-in-card
- card-mod
- apexcharts-card

---

### 3. Add images 🖼️

Download the 7 images and put them in `/config/www/passat/`:

| File | Description |
|------|-------------|
| `none.png` | Vehicle unplugged |
| `full.png` | Vehicle plugged |
| `charging.png` | Charging |
| `heat_plugged.png` | Heating active + plugged |
| `heat_unplugged.png` | Heating active + unplugged |
| `clim_plugged.png` | Cooling active + plugged |
| `clim_unplugged.png` | Cooling active + unplugged |

> 💡 Images are available at `/local/passat/` in Lovelace

---

### 4. Import the dashboard and go! 🚀

1. Go to **Settings** → **Dashboards**
2. Create a new dashboard
3. Switch to YAML mode (⋮ → Edit in YAML)
4. Paste the content of `passat-gte-dashboard.yaml`

---

### 5. Credits 

- [CarConnectivity](https://github.com/tillsteinbach/CarConnectivity) by tillsteinbach
- Tested with Volkswagen Passat GTE 2018

---
