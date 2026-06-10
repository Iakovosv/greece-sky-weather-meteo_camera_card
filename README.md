# 🌤️ Greece Sky and Weather Card v3.3

**by Iakovos Venieris** - Home Assistant Lovelace Card

**Production-Ready with Plugin Isolation & HACS-Submission Ready**

---

## v3.3 Changes (from v3.2)

| Fix | Description |
|-----|-------------|
| 🔒 **Plugin Isolation** | Auto-disable after 3 errors |
| 📦 **Single Source** | `/dist/` folder for HACS |
| 🌐 **Scoped Exports** | `window.GSCard` (no pollution) |
| ⚡ **Performance Modes** | normal / low-power throttling |
| 🛡️ **Error Resilience** | Try/catch on all lifecycle hooks |
| ✅ **HACS Ready** | Proper metadata, codeowner |

---

## Installation

### HACS (Recommended)
Search "Greece Sky" in HACS → Install

### Manual
1. Copy `dist/meteo-camera-card.js` to `/config/www/`
2. Settings → Dashboards → Resources → Add
   - URL: `/local/dist/meteo-camera-card.js`
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
  azimuth: 0
plugins:
  alerts: true
```

---

## Performance Modes

```yaml
# Normal mode (default)
performance_mode: normal

# Low-power mode (reduce polling)
performance_mode: low-power
```

Low-power mode throttles state updates to 1/second for battery-saving.

---

## Plugin System (v3.3)

### Plugin Isolation
Plugins automatically disable after 3 consecutive errors:
```javascript
class MyPlugin extends MeteoPlugin {
  static pluginName = 'my-plugin';
  _maxErrors = 3; // Auto-disable threshold
}
```

### Scoped Export
```javascript
window.GSCard.MeteoPlugin
window.GSCard.WindEngine
window.GSCard.PluginRegistry
```

---

## Configuration

### Entities
| Entity | Description |
|--------|-------------|
| `wind_direction` | Wind direction (0-360) |
| `wind_speed` | Wind speed |
| `wind_gust` | Wind gust |
| `temperature` | Temperature |
| `humidity` | Humidity |
| `rain` | Rain |
| `pressure` | Pressure |

### Camera Options
| Option | Default | Description |
|--------|---------|-------------|
| `camera.azimuth` | 0 | Camera direction |
| `camera.show_compass` | true | Show compass |
| `camera.camera_proxy` | true | Use HA proxy |

### Display Options
| Option | Default | Description |
|--------|---------|-------------|
| `display.arrow_color` | #00BFFF | Arrow color |
| `display.arrow_size` | 50 | Arrow size (px) |
| `display.card_height` | 280px | Card height |
| `display.gust_threshold` | 2.0 | Gust threshold |

---

## Architecture

```
Greece Sky v3.3
├── /dist/meteo-camera-card.js  (single source)
├── Scoped export: window.GSCard
├── Plugin isolation (auto-disable)
├── EMA smoothing (time-weighted)
└── Performance modes
```

---

## Technical Specs

- ✅ Plugin isolation (3 errors = disable)
- ✅ Scoped exports (no global pollution)
- ✅ Performance modes (normal/low-power)
- ✅ EMA smoothing (time-weighted)
- ✅ Error resilience (all lifecycle hooks)
- ✅ Single source distribution
- ✅ HACS metadata v3.3
- ✅ Codeowner: @iakovos

---

**v3.3** - Greece Sky · Iakovos Venieris
