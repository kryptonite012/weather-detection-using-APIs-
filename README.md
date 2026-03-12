# 🇮🇳 भारत WeatherSync — Indian Cities Weather & AQI Dashboard

A production-grade, zero-dependency weather dashboard for Indian cities
built with **vanilla HTML/CSS/JS** and powered by free Open-Meteo APIs.

---

## ✨ Features

- ⚡ **Concurrent fetching** via `Promise.allSettled()` — all 3 cities load in parallel
- 🌤️ **Live weather data** — temperature, feels like, humidity, wind speed, condition
- 🫁 **AQI (Air Quality Index)** — European AQI with PM₂.₅, PM₁₀, NO₂ pollutants
- 🎨 **Color-coded AQI bar** — Good → Fair → Moderate → Poor → Very Poor → Hazardous
- 🇮🇳 **India-first geocoding** — prefers `country_code = IN` so Indian city names resolve correctly
- 🕐 **Live IST clock** in the header
- 💀 **Skeleton loading** + per-card error handling (one failed city doesn't break others)
- 📱 **Fully responsive** — works on mobile, tablet, desktop
- 🚫 **Zero dependencies** — single `.html` file, no npm, no build step

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Language | Vanilla HTML5 / CSS3 / JavaScript (ES2020) |
| Weather API | [Open-Meteo Forecast API](https://open-meteo.com) |
| AQI API | [Open-Meteo Air Quality API](https://open-meteo.com/en/docs/air-quality-api) |
| Geocoding | [Open-Meteo Geocoding API](https://geocoding-api.open-meteo.com) |
| Concurrency | `Promise.allSettled()` |
| Fonts | Google Fonts — Plus Jakarta Sans + JetBrains Mono |

---

## 🚀 Getting Started

No installation needed. Just open the file:
```bash
git clone https://github.com/YOUR_USERNAME/india-weather-dashboard.git
cd india-weather-dashboard
open index.html   # or double-click the file
```

Or deploy instantly to **GitHub Pages**, **Netlify**, or **Vercel** — it's a single static file.

---

## 🏙️ Supported Cities

Any Indian city works — just type in the input fields. Defaults:

- 🏛️ Delhi
- 💰 Mumbai  
- 🌸 Bengaluru

Other examples: `Chennai`, `Kolkata`, `Hyderabad`, `Pune`, `Ahmedabad`, `Jaipur`, `Lucknow`

---

## 📡 How It Works
```
User clicks "Fetch All"
       │
       ├─ Promise.allSettled([
       │     fetchWeatherAndAQI("Delhi"),     ← geocode → weather + AQI (parallel)
       │     fetchWeatherAndAQI("Mumbai"),    ← geocode → weather + AQI (parallel)
       │     fetchWeatherAndAQI("Bengaluru")  ← geocode → weather + AQI (parallel)
       │  ])
       │
       └─ All 3 settle → render cards (errors shown per-card, not full crash)
```

Each city makes **3 API calls in parallel** internally:
1. Geocoding API → coordinates
2. Forecast API → weather data
3. Air Quality API → AQI + pollutants

---

## 🌈 AQI Scale Reference

| AQI Range | Level | Color |
|---|---|---|
| 0 – 20 | Good | 🟢 Green |
| 21 – 40 | Fair | 🟡 Yellow-Green |
| 41 – 60 | Moderate | 🟡 Amber |
| 61 – 80 | Poor | 🟠 Orange |
| 81 – 100 | Very Poor | 🔴 Red |
| 101 – 150 | Extremely Poor | 🟣 Purple |
| 150+ | Hazardous | 🟣 Dark Purple |

---

## 📸 Preview

> Live weather cards with saffron–white–green tricolor theme inspired by 🇮🇳

---

## 📜 License

MIT — free to use, modify, and distribute.

---

## 🙏 Credits

- Weather & AQI data — [Open-Meteo](https://open-meteo.com) (free, no API key required)
- Fonts — [Google Fonts](https://fonts.google.com)
