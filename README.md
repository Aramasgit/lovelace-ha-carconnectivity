# lovelace-ha-carconnectivity
🚗 Carconnectivity Dashboard for Home Assistant

A modern and elegant Home Assistant dashboard to monitor and control your CarConnectivity compatible car.

## Preview 📸

<p align="center">
  <img width="1087" height="618" alt="heating" src="https://github.com/user-attachments/assets/7d59a18c-4c06-4ae3-8e6e-f0ab93aa2b4e" />
</p>


---

### 1. Features ✨

🖼️ Dynamic images - 7 different visual states for your vehicle

🔋 Dynamic gauges - Battery and fuel with adaptive colors

🌡️ Smart climate control - Shows Heating/Cooling/Ventilation based on temperature

⚡ Charging management - Control socket and vehicle charging

🎚️ Amperage selection - Buttons for 5A, 10A, 13A, 16A

📊 24h history - Battery and fuel graph

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

---

### 4. Configure MQTT entities 

> ⚠️ **Why this file?**  
> CarConnectivity normally supports Home Assistant MQTT auto-discovery, which automatically creates all entities. However, this feature doesn't work reliably with my setup. I don't know why.  
> 
> This MQTT configuration file manually defines all the entities used by the dashboard. Simply replace `VIN_OF_YOUR_CAR` with your actual VIN.

1. Copy `mqtt_carconnectivity.yaml` to your Home Assistant config folder
2. Replace `VIN_OF_YOUR_CAR` with your actual VIN (use Find & Replace)
3. Include it in your `configuration.yaml`:
```yaml
mqtt: !include mqtt_carconnectivity.yaml
```

4. Restart Home Assistant

> 💡 This file creates all sensors, binary_sensors, switches, buttons and numbers needed for the dashboard.

---

### 5. Import the dashboard and go! 🚀

1. Go to **Settings** → **Dashboards**
2. Create a new dashboard
3. Switch to YAML mode (⋮ → Edit in YAML)
4. Paste the content of `passat-gte-dashboard.yaml`
5. Update the entities to match your setup (see below)

---

### 6. Optional entities 🔧

These entities are **not** included in the MQTT file ( `mqtt_carconnectivity.yaml` ) and must be created separately:

| Entity | Description | Source |
|--------|-------------|--------|
| `switch.switch_ve` | Smart plug for charger | Tuya, Shelly, etc. |
| `sensor.switch_ve_electric_consumption_w` | Power consumption (W) | Smart plug |
| `sensor.temp_outside_temperature` | Outside temperature | Weather integration |
| `automation.passat_degivrage_hiver` | Winter defrost automation | Your automation |

> 💡 If you don't have these, remove or comment out the related sections in the dashboard YAML.
> 
---

### 7. Optional: Winter Defrost Automation ❄️

This automation starts the climate at 21°C with window heating for quick defrosting AND restart CarConnectivity container.

**Why restart the container?**  
CarConnectivity may not immediately reflect state changes in Home Assistant. Restarting the container forces a refresh.

**Setup:**

1. Import `automation_winter_defrost.yaml`
2. Update the automation with your VIN
3. Add shell command to `configuration.yaml`:
```yaml
shell_command:
  restart_carconnectivity: "docker restart carconnectivity"
```

4. Ensure Home Assistant has Docker permissions

---
   
### 8. Credits 

- [CarConnectivity](https://github.com/tillsteinbach/CarConnectivity) by tillsteinbach
- Tested with Volkswagen Passat GTE 2018

---
