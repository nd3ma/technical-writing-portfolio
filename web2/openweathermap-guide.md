# How to Get Current Weather Data Using the OpenWeatherMap API

## Introduction

This guide shows you how to retrieve real-time weather data for any city using the OpenWeatherMap API. You will learn how to get an API key, make a request, and understand the response.

**Who this is for:** Developers who want to add weather information to their applications.

## Prerequisites

- Basic knowledge of HTTP requests and JSON
- A free OpenWeatherMap account

## Step 1: Get Your API Key

1. Go to [OpenWeatherMap](https://openweathermap.org/) and create a free account.
2. Navigate to your API keys section.
3. Copy your default API key (or generate a new one).

> **Note:** It may take a few minutes for a new API key to become active.

## Step 2: Make a Request

### Endpoint

### Required Parameters

| Parameter | Description              | Example     |
|-----------|--------------------------|-------------|
| `q`       | City name                | `London`    |
| `appid`   | Your API key             | `your_key`  |
| `units`   | Units of measurement     | `metric`    |

### Example Request (cURL)

```bash
curl "https://api.openweathermap.org/data/2.5/weather?q=London&appid=YOUR_API_KEY&units=metric"

Step 3: Understand the Response
A successful response returns a JSON object. Here are the most useful fields:
Field
Description
name
City name
main.temp
Temperature (in selected units)
main.humidity
Humidity percentage
weather[0].description
Weather condition (e.g. "clear sky")
wind.speed
Wind speed

Example response(simplified)
{
  "name": "London",
  "main": {
    "temp": 18.5,
    "humidity": 72
  },
  "weather": [
    {
      "description": "broken clouds"
    }
  ],
  "wind": {
    "speed": 4.1
  }
}
Error Handling
Status Code
Meaning
200
Success
401
Invalid API key
404
City not found
429
Too many requests (rate limit)
Always check the response status and handle errors gracefully in your application.Quick API Reference
Method
Endpoint
Description
GET
/data/2.5/weather?q={city}&appid={API_key}
Get current weather by city
Next Steps
Try requesting weather by geographic coordinates (lat & lon)
Explore the 5-day forecast endpoint
Add error handling and loading states in your UI