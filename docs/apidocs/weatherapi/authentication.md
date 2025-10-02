# Authentication

The OpenWeather API requires an **API key** for all requests.  
This key identifies you and ensures fair usage across the platform.

## Obtaining an API Key
1. Create a free account at [OpenWeather](https://home.openweathermap.org/users/sign_up).
2. Log in to your [dashboard](https://home.openweathermap.org/api_keys).
3. Generate a new API key.
4. Copy and securely store your key (you’ll need it for every request).


##  How to Use the API Key

The API key must be included as the `appid` query parameter in each request.

**Example**

```bash
curl "https://api.openweathermap.org/data/2.5/weather?q=London&appid=YOUR_API_KEY"
```


### Using Units

You can specify the unit system with the `units` parameter:

* `standard` (default, Kelvin)
* `metric` (Celsius)
* `imperial` (Fahrenheit)

**Example**

```bash
curl "https://api.openweathermap.org/data/2.5/weather?q=London&units=metric&appid=YOUR_API_KEY"
```


### Example Response (sample)

```json
{
  "coord": { "lon": 36.8219, "lat": -1.2921 },
  "weather": [
    { "main": "Clear", "description": "clear sky" }
  ],
  "main": {
    "temp": 26.5,
    "humidity": 54
  },
  "name": "London"
}
```

##  Best Practices

* **Do not share your key** in public repositories or client-side code.
* Rotate keys periodically for security.
* Monitor usage in your OpenWeather dashboard.
* Use environment variables to store your API key in projects.


##  FAQs

**Q: Can I pass the key as a header instead of query param?**
A: No. The OpenWeather API only supports the `appid` query parameter.

**Q: Can I have multiple API keys?**
A: Yes, you can generate more than one key in your dashboard.

**Q: What if I lose my API key?**
A: You can revoke and generate a new one from your OpenWeather account.

