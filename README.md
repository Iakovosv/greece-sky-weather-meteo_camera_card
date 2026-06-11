# 🌤️ Greece Sky and Weather Card v4.0

**by Iakovos Venieris** - Home Assistant Lovelace Card

---

## v4.0 Features

| Feature | Description |
|---------|-------------|
| 🎯 **Click to Expand** | Click card to see full-size camera image |
| 📍 **Arrow Position** | Full control: top, left, right, bottom |
| 🧭 **Azimuth Position** | Full control: top, right, left, bottom |
| 🧭 **Compass North** | Red needle always points North (N) |
| 📐 **Wind Direction** | Arrow shows WHERE wind is going (360°) |
| 📐 **Data Size** | small / medium / large |
| 📷 **Show/Hide Camera** | Toggle camera visibility |

---

## How It Works

### 🧭 Compass (Azimuth)
- Red half of needle **always points North**
- Use `camera.azimuth` to set your camera direction

### 🔽 Wind Arrow
- Shows **WHERE the wind is going** (opposite of wind source)
- Respects your camera azimuth for accurate positioning
- Full 360° rotation based on wind direction

**Example:**
- Wind from North (0°) → Arrow points South (towards the sea/south)
- Camera looking South-West (250°) → Arrow adjusts accordingly

### 📊 Wind Label
- Shows direction: Β, ΒΑ, Α, ΝΑ, Ν, ΝΔ, Δ, ΒΔ (and intermediate)
- 16 directions (every 22.5°)

---

## Installation

### HACS (Recommended)
Search "Greece Sky" in HACS → Install

### Manual
1. Copy `meteo-camera-card.js` to `/config/www/`
2. Settings → Dashboards → Resources → Add
   - URL: `/local/meteo-camera-card.js`
   - Type: module

---

## Quick Start

```yaml
type: custom:meteo-camera-card
camera_entity: camera.your_camera
entities:
  wind_direction: sensor.wind_direction
  wind_speed: sensor.wind_speed
  wind_gust: sensor.wind_gust
  temperature: sensor.temperature
  humidity: sensor.humidity
camera:
  azimuth: 250  # Camera direction (0-360°)
display:
  arrow_color: '#00BFFF'
```

---

## Configuration Options

### 📍 Camera

| Option | Default | Description |
|--------|---------|-------------|
| `camera_entity` | - | Camera entity |
| `camera.azimuth` | 0 | Camera direction (0-360°, 0=North) |

### 🔽 Arrow (Wind Direction)

| Option | Default | Description |
|--------|---------|-------------|
| `display.arrow_color` | #00BFFF | Arrow color |
| `display.arrow_size` | 50 | Arrow length (px) |
| `display.arrow_top` | 20% | Vertical position |
| `display.arrow_left` | 50% | Horizontal position |

### 🧭 Azimuth (Compass)

| Option | Default | Description |
|--------|---------|-------------|
| `display.show_azimuth` | true | Show compass |
| `display.azimuth_size` | 50 | Compass size (px) |
| `display.azimuth_top` | 12px | Vertical position |
| `display.azimuth_right` | 12px | Horizontal position |

### 📊 Data Panel

| Option | Default | Description |
|--------|---------|-------------|
| `display.data_size` | medium | small / medium / large |
| `display.panel_opacity` | 0.75 | Background opacity |

### 📷 Camera Display

| Option | Default | Description |
|--------|---------|-------------|
| `display.show_camera` | true | Show/hide camera |
| `display.click_to_expand` | true | Click to enlarge |

### 🎨 General

| Option | Default | Description |
|--------|---------|-------------|
| `display.card_height` | 280px | Card height |
| `display.gust_threshold` | 2.0 | Gust alert threshold |
| `display.temperature_unit` | °C | Temperature unit |
| `display.speed_unit` | km/h | Speed unit |

---

## Examples

### Weather Station with Camera
```yaml
type: custom:meteo-camera-card
camera_entity: camera.front_door
camera:
  azimuth: 250
display:
  arrow_color: '#00BFFF'
  arrow_size: 60
  show_azimuth: true
  azimuth_size: 45
  data_size: 'medium'
  click_to_expand: true
entities:
  wind_direction: sensor.wind_direction
  wind_speed: sensor.wind_speed
  wind_gust: sensor.wind_gust
  temperature: sensor.temperature
  humidity: sensor.humidity
```

### Compact Weather Display
```yaml
type: custom:meteo-camera-card
camera:
  azimuth: 180
display:
  show_camera: false
  data_size: 'large'
  card_height: '150px'
entities:
  wind_direction: sensor.wind_direction
  wind_speed: sensor.wind_speed
  temperature: sensor.temperature
```

---

## Performance Modes

```yaml
# Normal mode (default)
performance_mode: normal

# Low-power mode (1 update/second)
performance_mode: low-power
```

---

## ⚖️ Άδεια Χρήσης

**© Iakovos Venieris - All Rights Reserved**

⛔ **ΑΠΑΓΟΡΕΥΕΤΑΙ ΑΥΣΤΗΡΑ:**
- Η εμπορική χρήση χωρίς γραπτή άδεια
- Η τροποποίηση του κώδικα
- Η αναδημοσίευση σε άλλα projects

📧 Για άδειες: επικοινωνήστε με τον δημιουργό

---

**v4.0** - Greece Sky · Iakovos Venieris
