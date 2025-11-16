# WeatherX API Documentation

## Overview
WeatherX API allows developers to fetch real-time weather data, forecasts, and alerts for cities around the world.  
The API is organized around REST and uses standard HTTP methods and JSON responses.

---

## Base URL
```
https://api.weatherx.com/v1
```

All endpoints should be appended to the base URL.  
Example:
```
GET /weather?city=Lagos → https://api.weatherx.com/v1/weather?city=Lagos
```

---

## Authentication
WeatherX uses Bearer Token authentication. Include your API key in the `Authorization` header.

### Example:
```
Authorization: Bearer YOUR_API_KEY
```

### Invalid or missing API key response:
```json
{
  "error": "Invalid API key",
  "code": 401
}
```

---

# Endpoints

## 1. Get Current Weather
### `GET /weather?city={city_name}`

Returns current weather for a specified city.

### Example Request:
```
GET /weather?city=Lagos
```

### Successful Response:
```json
{
  "city": "Lagos",
  "temperature": 31,
  "humidity": 65,
  "description": "Partly cloudy"
}
```

---

## 2. Get 7-Day Forecast
### `GET /forecast?city={city_name}`

Returns a 7-day weather forecast for a city.

### Example Request:
```
GET /forecast?city=London
```

### Successful Response:
```json
{
  "city": "London",
  "forecast": [
    {"day": "Monday", "temperature": 18, "description": "Sunny"},
    {"day": "Tuesday", "temperature": 16, "description": "Rainy"}
  ]
}
```

---

## 3. Get Weather Alerts
### `GET /alerts?city={city_name}`

Returns any active weather alerts for the city.

### Example Request:
```
GET /alerts?city=New York
```

### Successful Response:
```json
{
  "city": "New York",
  "alerts": [
    {"type": "Storm Warning", "severity": "High"}
  ]
}
```

---

# Error Codes

| Code | Meaning |
|------|---------|
| **400** | Bad request |
| **401** | Unauthorized |
| **403** | Forbidden |
| **404** | Not found |
| **429** | Too many requests |
| **500** | Server error |

### Example Error Response:
```json
{
  "error": "City parameter missing",
  "code": 400
}
```

---

# Rate Limits
WeatherX API limits requests to:
```
60 requests per minute
```

### Rate Limit Response:
```json
{
  "error": "Too many requests",
  "code": 429
}
```

---

# Support
For assistance, contact:  
**support@weatherx.com**
