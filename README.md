# What's the Weather Like?

### Paul G. Arias, Ph.D.

### Summary of results

1) No observable trends for humidty, cloud overcast, and windspeed. 
2) Temperature is highest near equatorial regions. 
3) Northern hemisphere (positive latitudes) is in winter.

### Methodology

In order to find out some general trends about global weather behavior, I use an API called [OpenWeatherMap API][OWMAPI] to get weather data and a python library called [CitiPy][citipy] to get a city, given spatial coordinates.

To get a grid of spatial coordinates, I used the following code:

```python
long_range = np.linspace(-180,179,100)
lat_range = np.linspace(-90,89,100)
```
which creates a grid of evenly spaced coordinates grids. This allows us to create two for loops and provide the coordinates to the [CitiPy][citipy] library and get a nearby city:

```python
for lon in long_range:
    for lat in lat_range:
        city = citipy.nearest_city(lon,lat)
```

Further details on getting clean data is provided in the [Analysis notebook][notebook]

### Scatter plots

![temp]

The obvious trend that we observe is that the temperrature is generally high near the lower valued latitudes. Due to planetary tilt, the north and southern hemispheres experience seasons that vastly change the amount of radiant flux from the sun. This results in colder temperatures in the northern hemisphere (positive latitudes, winter) than in the southern hemisphere (which is, at the time of these measurements, in summer).

The clouds, humidity and windspeed data dont appear to reveal much information. We can observe that there are no major tropical storms near the selected cities occurring at this time, since windspeeds at ground level appear to be below 70 mph. 

![clouds]



![humidity]



![windspeed]


[OWMAPI]: https://openweathermap.org/api
[citipy]: https://github.com/wingchen/citipy/blob/master/README.md
[temp]: figures/Temperature.png
[clouds]: figures/Clouds.png
[humidity]: figures/Humidity.png
[windspeed]: figures/Windspeed.png
[notebook]: Analysis.ipynb
