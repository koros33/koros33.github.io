# Forecast

The **Forecast endpoint** provides 5-day weather data in 3-hour intervals.  
It returns temperature, humidity, wind, clouds, and weather conditions for each time step.



## 🌍 Endpoint
```

GET /forecast

```

Base URL:
```

[https://api.openweathermap.org/data/2.5/forecast](https://api.openweathermap.org/data/2.5/forecast)

````


## 🔧 Parameters

| Name      | Type   | Required | Description |
|-----------|--------|----------|-------------|
| `q`       | string | Yes (if no coordinates/zip) | City name (e.g. `"London"`) |
| `lat`     | float  | Yes (if no city name/zip)   | Latitude coordinate |
| `lon`     | float  | Yes (if no city name/zip)   | Longitude coordinate |
| `zip`     | string | Optional | Zip/postal code + country code (e.g. `94040,us`) |
| `cnt`     | int    | Optional | Number of forecast records to return (max 40) |
| `units`   | string | Optional | Unit system: `standard` (Kelvin), `metric` (°C), `imperial` (°F) |
| `lang`    | string | Optional | Language for weather description |
| `appid`   | string | Yes      | Your API key |


## 📌 Example Requests

### By City Name
```bash
curl "https://api.openweathermap.org/data/2.5/forecast?q=London&units=metric&appid=YOUR_API_KEY"
````

### By Coordinates

```bash
curl "https://api.openweathermap.org/data/2.5/forecast?lat=-1.2921&lon=36.8219&units=metric&appid=YOUR_API_KEY"
```

### Limit Records

```bash
curl "https://api.openweathermap.org/data/2.5/forecast?q=London&cnt=5&appid=YOUR_API_KEY"
```


## 📤 Example Response (sample)

```json
{
  "city": {
    "id": 184745,
    "name": "London",
    "coord": { "lat": -1.2921, "lon": 36.8219 },
    "country": "UK"
  },
  "list": [
    {
      "dt": 1696174800,
      "main": {
        "temp": 24.7,
        "feels_like": 25.0,
        "pressure": 1015,
        "humidity": 60
      },
      "weather": [
        { "description": "scattered clouds", "icon": "03d" }
      ],
      "clouds": { "all": 40 },
      "wind": { "speed": 2.5, "deg": 150 },
      "dt_txt": "2025-10-01 12:00:00"
    }
  ]
}
```


## 📝 Notes

* The **maximum forecast horizon** is **5 days / 40 records** (3-hour steps).
* Use `cnt` to limit the number of results (useful for small apps or dashboards).
* `lang` parameter helps localize weather descriptions by language.

---

## ⚡ Common Use Cases

* Build a 5-day weather forecast dashboard.
* Add forecast data to a mobile weather app.
* Display upcoming conditions for travel or events.

