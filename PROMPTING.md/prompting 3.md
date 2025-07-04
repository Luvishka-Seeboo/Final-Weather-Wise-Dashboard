---
## Initial Prompt 3
---
----------------------------------
Tool: ChatGPT
Date: 2025-05-22
----------------------------------
Me: I'm getting an error when calling the OpenWeatherMap API.

AI: Can you share the exact error message?

Me: Sure, it says: "requests.exceptions.HTTPError: 401 Client Error: Unauthorized".

```python
def get_weather_forecast(location, api_key):
    try:
        # Geocoding to get lat/lon
        geo_url = f"http://api.openweathermap.org/geo/1.0/direct?q={location}&limit=1&appid={api_key}"
        geo_response = requests.get(geo_url)
        geo_data = geo_response.json()

        if not geo_data:
            return None, f"❌ Location '{location}' not found. Please check spelling."

        lat = geo_data[0]['lat']
        lon = geo_data[0]['lon']
        city = geo_data[0]['name']
        country = geo_data[0]['country']

        # Get 5-day forecast
        forecast_url = f"https://api.openweathermap.org/data/2.5/forecast?lat={lat}&lon={lon}&units=metric&appid={api_key}"
         forecast_data = requests.get(forecast_url).json()
```
AI: That usually means the API key is missing or invalid. Are you passing your API key correctly in the request?

Me: I'm using this line: params = {"q": f"{city},MU", "appid": api_key, "units": "metric"}

AI: That looks correct syntactically. Can you double-check if your `api_key` variable actually contains your API key?

Me: Hmm, I might have left it blank during testing.

AI: That would explain it. Try printing `api_key` before the request to verify. Also, make sure you’re not using expired or incorrect credentials.

Me: Okay, I’ll check.

AI: If you're using a widget, make sure to click the “Show Weather” button after entering the API key. The value must be captured before the request executes.

Me: Got it. It’s working now. Thanks!
