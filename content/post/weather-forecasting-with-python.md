---
title: "Weather Report and Forecasting with Python"
date: "2015-11-13T01:54:46+01:00"
description: "Example article description"
draft: false

#thumbnail: "img/placeholder.jpg" # Optional, thumbnail
#lead: "Example lead - highlighted near the title"
disable_comments: false # Optional, disable Disqus comments if true
authorbox: true # Optional, enable authorbox for specific post
toc: false # Optional, enable Table of Contents for specific post
mathjax: true # Optional, enable MathJax for specific post
categories:
  - "Embedded Systems"
tags:
  - "Programming"
#menu: main # Optional, add page to a menu. Options: main, side, footer
---

OpenWeatherMap.org is a free weather forecast website, where you can get up-to-date weather reports. One nice thing about this website is that it does provide weather APIs which you can use to fetch current weather data, and use them to build your own weather-forecasting program. In this post, I will describe how to use python to access the weather APIs and fetch the current weather information.

The full documentation of the APIs can be find here: <http://openweathermap.org/api>. To access the APIs, you have to register a new account to obtain an API key. There are two categories of APIs that can be used for free: Current and 5 day forecast. The Current API provides up-to-date weather data, which includes current temperature, humidity, wind, etc. The 5 day forecast gives information of the weather data for the next 5 days in every 3 hours. So you will get 40 forecasts in total. The usage of the APIs is simple, just send request to specific URLs, and get data in return given in the form of json or XML.

Here I give an example of how to use the Current API:

a) Fetch data from the URL provided by the document:

```python
# this is where you should put your OpenWeatherMap API key
# get your own key from http://openweathermap.org/
API_KEY = "5eb19937b8ba9aa2029fe7e290b8d799"

# this is the city you want to enquiry
CITY_NAME = "York,uk"

# get weather data from weather.com
try:
    f = urllib2.urlopen('http://api.openweathermap.org/data/2.5/weather?q=' \
                    + CITY_NAME + '&units=metric' + '&APPID=' +  API_KEY)
    respond_raw = f.read()
except:
        print 'Execption: URL is not correct!'
        raise
```

b) The default data format is json, we can unpack it with the json library:

```python
# unpack json package into python dictionary
weather_dict = json.loads(respond_raw)

# print raw data with pprint
pp.pprint(weather_dict)
```

what you will get is something like this:

```python
{   u'base': u'cmc stations',
    u'clouds': {   u'all': 36},
    u'cod': 200,
    u'coord': {   u'lat': 53.96, u'lon': -1.08},
    u'dt': 1447431162,
    u'id': 2633352,
    u'main': {   u'grnd_level': 1016.58,
                 u'humidity': 89,
                 u'pressure': 1016.58,
                 u'sea_level': 1027.66,
                 u'temp': 6.99,
                 u'temp_max': 6.99,
                 u'temp_min': 6.99},
    u'name': u'York',
    u'sys': {   u'country': u'GB',
                u'message': 0.0106,
                u'sunrise': 1447399715,
                u'sunset': 1447430881},
    u'weather': [   {   u'description': u'scattered clouds',
                        u'icon': u'03n',
                        u'id': 802,
                        u'main': u'Clouds'}],
    u'wind': {   u'deg': 257.001, u'speed': 10.62}}
```

c) Once you have the data stored in a python dictionary, you can generate something more readable and customized:

```python
# print human-readable weather message
print('\n\n' + weather_dict['name'] + ' is ' + \
      weather_dict['weather'][0]['description'] + \
      ', temperature: ' + str(weather_dict['main']['temp']) + \
      ', humidity: ' + str(weather_dict['main']['humidity']) + '%.' )
```

which produces:

`York is scattered clouds, temperature: 6.99, humidity: 89%.`

Accessing 5 days forecast is very similar. But personally I think that API is not very useful, because it packs every 3 hour weather data in a single entity. This means in order to give a day-wide forecast, you have to process the data a little bit (day info is consisted of 8 entities) to find out the maximum and minimum temperatures. Also if you get more than one forecasts spreading in different times of the day (e.g., sunshine between 13:00-18:00 but raining between 10:00-13:00), you have to consider how to fairly describe the weather on that particular day . Due to these issues, I didn’t spent more efforts on that but instead switch to other weather providers. If you are more interested in forecasting, just have a try and let me know if it works.

## Appendix. Full Python Code

weather_from_openweather.py

```python
#!/usr/bin/python

import os
import urllib2
import json
import pprint

pp = pprint.PrettyPrinter(indent=4)

# this is where you should put your OpenWeatherMap API key
# get your own key from http://openweathermap.org/
API_KEY = "5eb19937b8ba9aa2029fe7e290b8d799"

# this is the city you want to enquiry
CITY_NAME = "York,uk"

# get weather data from weather.com
try:
    f = urllib2.urlopen('http://api.openweathermap.org/data/2.5/weather?q=' \
                    + CITY_NAME + '&units=metric' + '&APPID=' +  API_KEY)
    respond_raw = f.read()
except:
        print 'Execption: URL is not correct!'
        raise

# unpack json package into python dictionary
weather_dict = json.loads(respond_raw)

# print raw data with pprint
pp.pprint(weather_dict)

# print human-readable weather message
print('\n\n' + weather_dict['name'] + ' is ' + \
      weather_dict['weather'][0]['description'] + \
      ', temperature: ' + str(weather_dict['main']['temp']) + \
      ', humidity: ' + str(weather_dict['main']['humidity']) + '%.' )
```
