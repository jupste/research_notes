---
title: Weather
created: '2021-07-05T08:06:38.882Z'
modified: '2021-07-05T10:20:35.485Z'
---

# Weather

Weather data is processed in GRIB format. Typically forecasts are provided 4 times per day at 6 hour intervals. GRIB data is provided as a set of messages that contain a set of set of coordinates. Each message contains 1280 sets of coordinates and each set contains 2560 elements. The latitudes an longitudes are in different arrays and the latitudes are always same in a given array and each longitude array is the same.

Weather data is requested through an API where the user can define what features they want from the data. There are over 5000 different features that the weather data can contain. Since we are interested mainly on the wind and wave data we can ommit most of these features. However this leaves us with several hundreds of features so we need to narrow this down even further based on domain knowledge. Each feature produces it's own GRIB message so the file size gets really large as the number features increases. Just two features over a month (120 messages) produces a dataset of over 1 GB size. 

The data acquired via commercial retailers seems to be relatively well formed. So there is likely little need to wrangle this data in any meaningful way. One question remains that should the weather data be combined with the AIS data. Since the weather at the location of the ship is less meaningful than the weather at the ships destination, combining these two datasets could be too complex for the wrangling operations. 


