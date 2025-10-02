# OpenWeather API Documentation

Welcome to the **OpenWeather API documentation**.  
This is a **simplified, portfolio-ready version** of the OpenWeather API, created to demonstrate clear technical documentation practices.  

You will find instructions on authentication, available endpoints, and error handling.  
For full API details, visit the [official OpenWeather docs](https://openweathermap.org/api).

---

##  What’s Covered
- [Authentication](authentication.md) – Learn how to use your API key.
- [Current Weather](current-weather.md) – Get real-time weather by city or coordinates.
- [Forecast](forecast.md) – Retrieve 5-day / 3-hour forecast data.
- [Error Codes](errors.md) – Understand possible error responses.
  

##  Getting Started

### Prerequisites
1. A free [OpenWeather account](https://home.openweathermap.org/users/sign_up).  
2. An API key (generated from your OpenWeather dashboard).  
3. A tool like **cURL**, **Postman**, or any HTTP client to make requests.  



### Base URL
All requests are made over HTTPS:
```

[https://api.openweathermap.org/data/2.5/](https://api.openweathermap.org/data/2.5/)

````



### Quick Example

Request current weather for Nairobi, Kenya (metric units):

```bash
curl "https://api.openweathermap.org/data/2.5/weather?q=London&units=metric&appid=YOUR_API_KEY"
````

Sample response (sample):

```json
{
  "weather": [
    { "main": "Clear", "description": "clear sky" }
  ],
  "main": {
    "temp": 26.5,
    "humidity": 54
  },
  "wind": { "speed": 3.6 },
  "name": "London"
}
```


##  FAQs

**Q: Is this the official OpenWeather API documentation?**
A: No. This is a simplified version created as a **portfolio sample for technical writing**.

**Q: Can I actually use these endpoints?**
A: Yes! The examples are real and based on OpenWeather’s free API. Just replace `YOUR_API_KEY` with a valid one.

**Q: What’s the rate limit?**
A: Free accounts are limited to **60 requests per minute** (check official docs for updated limits).

**Q: Why do I see errors when testing?**
A: Make sure you’ve included a valid `appid` parameter (your API key). See the [Error Codes](errors.md) page for details.


##  Next Steps

* [Set up authentication](authentication.md)
* Try the [Current Weather](current-weather.md) endpoint
* Explore the [Forecast](forecast.md) endpoint
* Review possible [Error Codes](errors.md)
