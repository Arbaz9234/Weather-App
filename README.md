<div align="center">

# 🌤️ Weather App

### *A responsive weather app powered by the OpenWeatherMap API — search any city, save your home location, and get a live 6-day forecast with dynamic backgrounds.*

<br/>

[![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![OpenWeatherMap](https://img.shields.io/badge/OpenWeatherMap_API-EB6E4B?style=for-the-badge&logo=openweathermap&logoColor=white)](https://openweathermap.org/api)
[![Font Awesome](https://img.shields.io/badge/Font_Awesome-528DD7?style=for-the-badge&logo=fontawesome&logoColor=white)](https://fontawesome.com)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
</div>

---

## ✨ Features

- 🔍 **Search** by city, state, country or zip code
- 📍 **Geolocation** — detect your current location automatically
- 🌡️ **Unit toggle** — switch between °F (imperial) and °C (metric)
- 📅 **6-day forecast** with daily high/low and weather icons
- 🌅 **Dynamic backgrounds** — changes based on weather conditions (rain, snow, fog, night, clouds)

---

## 🏗️ Architecture

```mermaid
flowchart TD
    U([🙋 User Input\nSearch / Geolocation / Home])
    U --> C

    subgraph C ["📍 CurrentLocation Class"]
        CT(" "):::spacer
        C1[Stores lat, lon, name, unit]
        C2[toggleUnit — imperial ↔ metric]
        CB(" "):::spacer
        CT ~~~ C1 --- C2 ~~~ CB
    end

    C --> D

    subgraph D ["📡 dataFunctions.js"]
        DT(" "):::spacer
        D1["getCoordsFromApi(text)\nCity/zip → lat & lon"]
        D2["getWeatherFromCoords(locationObj)\nOWM One Call API"]
        DB(" "):::spacer
        DT ~~~ D1 --> D2 ~~~ DB
    end

    D --> UI

    subgraph UI ["🖥️ OtherFunctions.js"]
        UT(" "):::spacer
        U1["updateDisplay()\nRender conditions + 6-day forecast"]
        U2["setBGImage()\nDynamic weather background"]
        U3["fadeDisplay()\nSmooth transitions"]
        UB(" "):::spacer
        UT ~~~ U1 & U2 & U3 ~~~ UB
    end

    UI --> R([✅ Live weather rendered\nwith dynamic background])

    classDef spacer fill:none,stroke:none,color:transparent
    style U fill:#1e3a5f,color:#a8d8ff,stroke:#4a9eff
    style R fill:#1a3d2b,color:#a8ffcc,stroke:#3ddc84
    style C fill:#1a1a2e,color:#e0e0ff,stroke:#4a4aff
    style D fill:#1a1a2e,color:#e0e0ff,stroke:#4a4aff
    style UI fill:#1a1a2e,color:#e0e0ff,stroke:#4a4aff
```

---


## 🚀 Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/your-username/weather-app.git
cd weather-app
```

### 2. Add your API key

In `dataFunctions.js`, replace the key:

```js
const WEATHER_API_KEY = 'your_openweathermap_api_key';
```

> Get a free key at [openweathermap.org](https://openweathermap.org/api). The app uses the **Current Weather** and **One Call** endpoints.

### 3. Open in browser

```bash
# No build step needed — open directly
open index.html
```

---

## 📁 Project Structure

```
weather-app/
│
├── javascript/weather javascript/
│   ├── main.js               # App init, event listeners, flow control
│   ├── dataFunctions.js      # API calls, location object helpers
│   ├── OtherFunctions.js     # DOM updates, display, animations
│   └── CurrentLocation.js    # Class — stores location & unit state
│
├── stylesheet/weather2 css/
│   └── main.min.css
│
├── weather scss/
│   └── main.css
│
└── index.html
```

---

## 🛠️ Tech

| | |
|---|---|
| **Language** | Vanilla JavaScript (ES6 Modules) |
| **API** | OpenWeatherMap — Current Weather + One Call |
| **Icons** | Font Awesome 5 |
| **Styling** | SCSS compiled to CSS |