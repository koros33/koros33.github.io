# Current Weather

The **Current Weather endpoint** provides real-time weather information for a given city, coordinates, or zip code.  
It returns temperature, humidity, pressure, wind speed, and general conditions.


## 🌍 Endpoint
```

GET /weather

```

Base URL:
```

[https://api.openweathermap.org/data/2.5/weather](https://api.openweathermap.org/data/2.5/weather)

````


## 🔧 Parameters

| Name      | Type   | Required | Description |
|-----------|--------|----------|-------------|
| `q`       | string | Yes (if no coordinates/zip) | City name (e.g. `"London"`) |
| `lat`     | float  | Yes (if no city name/zip)   | Latitude coordinate |
| `lon`     | float  | Yes (if no city name/zip)   | Longitude coordinate |
| `zip`     | string | Optional | Zip/postal code and country code (e.g. `94040,us`) |
| `units`   | string | Optional | Unit system: `standard` (Kelvin), `metric` (°C), `imperial` (°F) |
| `lang`    | string | Optional | Language for weather description (e.g. `en`, `es`, `fr`) |
| `appid`   | string | Yes      | Your API key |

---

## 📌 Example Requests

### By City Name
```bash
curl "https://api.openweathermap.org/data/2.5/weather?q=London&units=metric&appid=YOUR_API_KEY"
````

### By Coordinates

```bash
curl "https://api.openweathermap.org/data/2.5/weather?lat=-1.2921&lon=36.8219&appid=YOUR_API_KEY"
```

### By Zip Code

```bash
curl "https://api.openweathermap.org/data/2.5/weather?zip=94040,us&appid=YOUR_API_KEY"
```

---

## Example Response (sample)

```json
{
  "coord": { "lon": 36.8219, "lat": -1.2921 },
  "weather": [
    {
      "id": 800,
      "main": "Clear",
      "description": "clear sky",
      "icon": "01d"
    }
  ],
  "main": {
    "temp": 26.5,
    "feels like": 27.1,
    "pressure": 1013,
    "humidity": 54
  },
  "visibility": 10000,
  "wind": { "speed": 3.6, "deg": 90 },
  "clouds": { "all": 0 },
  "sys": {
    "country": "UK",
    "sunrise": 1696123456,
    "sunset": 1696166789
  },
  "name": ";London"
}
```


## 📝 Notes

* **Precision**: Coordinates are recommended when possible to avoid ambiguity.
* **Units**: Default is Kelvin unless `units` is specified.
* **Localization**: Use `lang` parameter to return weather descriptions in your preferred language.


## ⚡ Common Use Cases

* Display current conditions in a weather dashboard.
* Power a “What’s the weather now?” chatbot.
* Add live weather data to IoT apps.
