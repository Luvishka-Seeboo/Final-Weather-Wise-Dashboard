---

Title: Prompting Journey for Weather Data Retrieval Function

---

---
## Initial Prompt 1 
---
----------------------------------
Tool: ChatGPT
Date: 2025-05-22
----------------------------------


Me: Can you help me build a weather dashboard using Python and OpenWeatherMap API to show the weather in cities in Mauritius?
AI: Definitely! Let's break it into steps. The dashboard will include:

-A list of Mauritian cities (dropdown)

-Input for API key

-A button to fetch weather

-A visual layout with cards showing temperature, humidity, etc.

We’ll use:

-requests to get weather data

-ipywidgets for interactivity in a Jupyter Notebook

-Some HTML/CSS in widgets for styling

Let’s start with the data-fetching function.

```python
def get_weather(city, api_key):
    url = "https://api.openweathermap.org/data/2.5/weather"
    params = {"q": f"{city},MU", "appid": api_key, "units": "metric"}
    response = requests.get(url, params=params)
    return response.json()
```
