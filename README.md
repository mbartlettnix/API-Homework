
# WeatherPy

Analysis
1. Latitude closest to zero have the highest temperture. The deep slope on the positive side indicates that it is winter in the northen hemisphere
2. Humidity, Cloudiness and Wind speed do not appear to have an association with latitude
3. Although Wind Speed doesn't correlate with latitude, It does appear to have instances of higher Wind Speed nearing the North Pole. 


```python
import openweathermapy.core as ow
import numpy as np
import pandas as pd
import seaborn as sns
from scipy import stats
import matplotlib as mpl
import matplotlib.pyplot as plt
from citipy import citipy
```


```python
api_key = "d9f788ccd230de9dfedc79a53db72d7f"
settings = {"units": "imperial", "appid": api_key}
units = 'imperial'

############## REPLACE WHEN GLOBAL ENVIROMENT IS FIXED #############
# csv = pd.read_csv("cities.csv", dtype=str)
# cities = csv['City']
```


```python
#generate random citites and give names
lat = np.random.uniform(-90, 91, 500)
long = np.random.uniform(-180, 181,500)
cities = []

for coord in range(len(lat)):
#     weather_df.set_value(coord,'city_name',citipy.nearest_city(lat[coord], long[coord]).city_name)
#     weather_df.set_value(i,'country_code',citipy.nearest_city(lat_coord[i], lng_coord[i]).country_code)
#     weather_df.set_value(i,'latitude',round(lat_coord[i],4))
#     weather_df.set_value(i,'longitude',round(lng_coord[i],4))
    cities.append(citipy.nearest_city(lat[coord], long[coord]).city_name)

```


```python
weather_data= []
weather_csv = []
weather_count =0
for city in cities:
    try:
        weather_count = weather_count+1
        response = ow.get_current(city, **settings)
        print(str(weather_count)+" of "+ str(len(cities))+", "+city+", "+ow.BASE_URL+"weather?appid=" + api_key + \
              "&units" + units+ "&q=" + city)
        weather_data.append(response)
        weather_csv.append(str(weather_count)+" of "+ str(len(cities))+", "+city+", "+ow.BASE_URL+"weather?appid=" + api_key + "&units" + units+ "&q=" + city)
    except:
        print("Complete")
        
```

    1 of 500, bathsheba, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bathsheba
    2 of 500, bathsheba, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bathsheba
    3 of 500, hobart, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hobart
    4 of 500, atuona, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=atuona
    5 of 500, ippy, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=ippy
    6 of 500, griffith, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=griffith
    7 of 500, laguna, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=laguna
    8 of 500, tuatapere, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=tuatapere
    Complete
    10 of 500, narsaq, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=narsaq
    Complete
    12 of 500, ancud, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=ancud
    13 of 500, hobart, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hobart
    14 of 500, longyearbyen, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=longyearbyen
    15 of 500, busselton, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=busselton
    16 of 500, morondava, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=morondava
    Complete
    18 of 500, cape town, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=cape town
    19 of 500, busselton, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=busselton
    20 of 500, hilo, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hilo
    21 of 500, zalantun, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=zalantun
    22 of 500, petropavlovsk-kamchatskiy, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=petropavlovsk-kamchatskiy
    23 of 500, saint-philippe, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=saint-philippe
    24 of 500, mabaruma, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=mabaruma
    25 of 500, zhigansk, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=zhigansk
    26 of 500, riyadh, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=riyadh
    27 of 500, hermanus, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hermanus
    28 of 500, flin flon, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=flin flon
    29 of 500, cidreira, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=cidreira
    30 of 500, monticello, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=monticello
    Complete
    32 of 500, rikitea, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=rikitea
    33 of 500, salinopolis, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=salinopolis
    Complete
    35 of 500, pamanukan, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=pamanukan
    36 of 500, rikitea, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=rikitea
    37 of 500, sorong, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=sorong
    38 of 500, kununurra, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=kununurra
    39 of 500, cabo san lucas, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=cabo san lucas
    40 of 500, port elizabeth, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=port elizabeth
    41 of 500, saint pete beach, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=saint pete beach
    42 of 500, ilulissat, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=ilulissat
    43 of 500, muroto, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=muroto
    44 of 500, busselton, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=busselton
    45 of 500, vostok, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=vostok
    46 of 500, kapaa, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=kapaa
    47 of 500, avarua, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=avarua
    48 of 500, portland, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=portland
    Complete
    50 of 500, atuona, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=atuona
    51 of 500, yellowknife, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=yellowknife
    52 of 500, punta arenas, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=punta arenas
    53 of 500, arlit, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=arlit
    54 of 500, half moon bay, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=half moon bay
    55 of 500, nanortalik, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=nanortalik
    56 of 500, sitangkai, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=sitangkai
    57 of 500, vanimo, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=vanimo
    58 of 500, ushuaia, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=ushuaia
    Complete
    Complete
    61 of 500, cortez, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=cortez
    62 of 500, dingle, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=dingle
    63 of 500, paamiut, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=paamiut
    64 of 500, bengkulu, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bengkulu
    65 of 500, taoudenni, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=taoudenni
    66 of 500, arraial do cabo, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=arraial do cabo
    67 of 500, punta arenas, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=punta arenas
    68 of 500, busselton, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=busselton
    69 of 500, tasiilaq, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=tasiilaq
    70 of 500, toledo, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=toledo
    Complete
    72 of 500, rikitea, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=rikitea
    Complete
    74 of 500, ushuaia, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=ushuaia
    Complete
    76 of 500, pandan niog, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=pandan niog
    Complete
    78 of 500, bluff, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bluff
    79 of 500, kikwit, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=kikwit
    80 of 500, talnakh, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=talnakh
    81 of 500, mahebourg, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=mahebourg
    82 of 500, puerto baquerizo moreno, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=puerto baquerizo moreno
    83 of 500, tuktoyaktuk, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=tuktoyaktuk
    Complete
    85 of 500, mar del plata, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=mar del plata
    86 of 500, los llanos de aridane, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=los llanos de aridane
    87 of 500, kodiak, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=kodiak
    88 of 500, vaini, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=vaini
    89 of 500, tuburan, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=tuburan
    90 of 500, cape town, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=cape town
    91 of 500, constitucion, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=constitucion
    92 of 500, port macquarie, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=port macquarie
    93 of 500, albany, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=albany
    Complete
    Complete
    Complete
    97 of 500, rikitea, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=rikitea
    98 of 500, barrow, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=barrow
    99 of 500, grand gaube, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=grand gaube
    Complete
    101 of 500, shuangcheng, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=shuangcheng
    Complete
    103 of 500, margate, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=margate
    104 of 500, rikitea, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=rikitea
    105 of 500, ketchikan, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=ketchikan
    106 of 500, taltal, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=taltal
    107 of 500, hobart, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hobart
    108 of 500, luderitz, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=luderitz
    109 of 500, puerto penasco, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=puerto penasco
    110 of 500, katsuura, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=katsuura
    111 of 500, bengkulu, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bengkulu
    112 of 500, praia, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=praia
    113 of 500, punta arenas, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=punta arenas
    Complete
    115 of 500, avarua, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=avarua
    Complete
    117 of 500, jamestown, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=jamestown
    Complete
    119 of 500, bossangoa, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bossangoa
    120 of 500, tasiilaq, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=tasiilaq
    121 of 500, kodiak, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=kodiak
    122 of 500, bambous virieux, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bambous virieux
    Complete
    Complete
    Complete
    126 of 500, hamilton, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hamilton
    127 of 500, bressuire, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bressuire
    Complete
    129 of 500, fukue, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=fukue
    130 of 500, palmer, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=palmer
    131 of 500, mehamn, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=mehamn
    132 of 500, thompson, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=thompson
    Complete
    134 of 500, bathsheba, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bathsheba
    135 of 500, tautira, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=tautira
    136 of 500, alofi, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=alofi
    137 of 500, avarua, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=avarua
    138 of 500, port elizabeth, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=port elizabeth
    139 of 500, hobart, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hobart
    140 of 500, borogontsy, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=borogontsy
    141 of 500, hofn, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hofn
    142 of 500, butaritari, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=butaritari
    143 of 500, tuktoyaktuk, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=tuktoyaktuk
    144 of 500, harwich, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=harwich
    145 of 500, abha, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=abha
    146 of 500, imbituba, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=imbituba
    147 of 500, los llanos de aridane, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=los llanos de aridane
    Complete
    149 of 500, kodiak, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=kodiak
    Complete
    151 of 500, albany, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=albany
    152 of 500, te anau, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=te anau
    153 of 500, barrow, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=barrow
    154 of 500, north platte, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=north platte
    155 of 500, mehamn, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=mehamn
    156 of 500, popovo, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=popovo
    157 of 500, lasa, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=lasa
    158 of 500, atuona, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=atuona
    Complete
    160 of 500, punta arenas, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=punta arenas
    161 of 500, guaymango, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=guaymango
    162 of 500, arlit, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=arlit
    163 of 500, hami, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hami
    Complete
    165 of 500, vaini, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=vaini
    166 of 500, albany, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=albany
    167 of 500, yellowknife, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=yellowknife
    168 of 500, cedar city, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=cedar city
    169 of 500, castro, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=castro
    170 of 500, andenes, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=andenes
    Complete
    172 of 500, mount isa, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=mount isa
    Complete
    174 of 500, hwange, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hwange
    175 of 500, port-gentil, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=port-gentil
    176 of 500, poya, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=poya
    177 of 500, port lincoln, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=port lincoln
    178 of 500, darab, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=darab
    179 of 500, codrington, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=codrington
    180 of 500, kahului, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=kahului
    181 of 500, nizwa, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=nizwa
    182 of 500, mahebourg, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=mahebourg
    183 of 500, rochester, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=rochester
    184 of 500, abu dhabi, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=abu dhabi
    185 of 500, buraydah, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=buraydah
    186 of 500, dikson, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=dikson
    Complete
    188 of 500, tasiilaq, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=tasiilaq
    189 of 500, eyl, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=eyl
    190 of 500, benemerito de las americas, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=benemerito de las americas
    191 of 500, bluff, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bluff
    192 of 500, ushuaia, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=ushuaia
    193 of 500, kisangani, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=kisangani
    Complete
    Complete
    196 of 500, dikson, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=dikson
    197 of 500, atar, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=atar
    198 of 500, castro, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=castro
    199 of 500, mildura, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=mildura
    200 of 500, bredasdorp, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bredasdorp
    201 of 500, bethel, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bethel
    202 of 500, bankura, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bankura
    203 of 500, busselton, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=busselton
    204 of 500, bluefield, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bluefield
    Complete
    206 of 500, oussouye, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=oussouye
    207 of 500, mahebourg, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=mahebourg
    208 of 500, cumra, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=cumra
    209 of 500, kruisfontein, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=kruisfontein
    210 of 500, svetlogorsk, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=svetlogorsk
    Complete
    212 of 500, cuauhtemoc, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=cuauhtemoc
    213 of 500, puerto rico, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=puerto rico
    214 of 500, vaini, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=vaini
    215 of 500, ushuaia, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=ushuaia
    216 of 500, leningradskiy, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=leningradskiy
    217 of 500, sistranda, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=sistranda
    218 of 500, nome, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=nome
    219 of 500, bredasdorp, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bredasdorp
    220 of 500, punta arenas, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=punta arenas
    221 of 500, ushuaia, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=ushuaia
    222 of 500, yokadouma, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=yokadouma
    223 of 500, punta arenas, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=punta arenas
    224 of 500, cape town, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=cape town
    225 of 500, tuktoyaktuk, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=tuktoyaktuk
    226 of 500, bluff, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bluff
    227 of 500, jamestown, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=jamestown
    Complete
    229 of 500, myitkyina, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=myitkyina
    Complete
    Complete
    232 of 500, kapaa, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=kapaa
    233 of 500, carnot, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=carnot
    234 of 500, cape town, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=cape town
    Complete
    236 of 500, vaini, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=vaini
    237 of 500, tuktoyaktuk, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=tuktoyaktuk
    238 of 500, dikson, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=dikson
    239 of 500, bluff, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bluff
    240 of 500, punta arenas, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=punta arenas
    241 of 500, mahebourg, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=mahebourg
    242 of 500, vaini, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=vaini
    243 of 500, skjervoy, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=skjervoy
    244 of 500, new norfolk, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=new norfolk
    Complete
    246 of 500, aklavik, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=aklavik
    247 of 500, flinders, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=flinders
    248 of 500, busselton, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=busselton
    249 of 500, hobart, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hobart
    250 of 500, nome, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=nome
    Complete
    Complete
    253 of 500, kaspiysk, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=kaspiysk
    254 of 500, qaanaaq, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=qaanaaq
    255 of 500, saint george, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=saint george
    256 of 500, naze, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=naze
    257 of 500, rikitea, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=rikitea
    258 of 500, hermanus, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hermanus
    259 of 500, hobart, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hobart
    260 of 500, touros, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=touros
    261 of 500, punta arenas, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=punta arenas
    262 of 500, bluff, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bluff
    263 of 500, cherskiy, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=cherskiy
    264 of 500, iqaluit, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=iqaluit
    265 of 500, busselton, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=busselton
    266 of 500, khatanga, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=khatanga
    267 of 500, hilo, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hilo
    268 of 500, ilulissat, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=ilulissat
    269 of 500, rockhampton, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=rockhampton
    270 of 500, creston, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=creston
    271 of 500, atuona, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=atuona
    272 of 500, chumikan, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=chumikan
    273 of 500, guerrero negro, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=guerrero negro
    274 of 500, severobaykalsk, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=severobaykalsk
    275 of 500, bluff, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bluff
    276 of 500, cabo san lucas, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=cabo san lucas
    277 of 500, grand gaube, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=grand gaube
    278 of 500, goba, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=goba
    279 of 500, qaanaaq, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=qaanaaq
    280 of 500, dosso, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=dosso
    281 of 500, hobart, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hobart
    282 of 500, san cristobal, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=san cristobal
    Complete
    284 of 500, marawi, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=marawi
    285 of 500, yellowknife, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=yellowknife
    286 of 500, pisco, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=pisco
    287 of 500, uri, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=uri
    288 of 500, rikitea, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=rikitea
    289 of 500, castro, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=castro
    Complete
    Complete
    292 of 500, new norfolk, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=new norfolk
    Complete
    294 of 500, hirara, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hirara
    295 of 500, cabo san lucas, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=cabo san lucas
    296 of 500, aklavik, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=aklavik
    297 of 500, fortuna, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=fortuna
    298 of 500, altus, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=altus
    299 of 500, altamira, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=altamira
    300 of 500, nanortalik, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=nanortalik
    301 of 500, mahebourg, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=mahebourg
    302 of 500, sabya, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=sabya
    303 of 500, doha, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=doha
    Complete
    305 of 500, fairbanks, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=fairbanks
    306 of 500, bengkulu, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bengkulu
    307 of 500, qaanaaq, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=qaanaaq
    Complete
    309 of 500, lebu, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=lebu
    310 of 500, avarua, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=avarua
    311 of 500, busselton, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=busselton
    312 of 500, alice springs, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=alice springs
    313 of 500, castro, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=castro
    314 of 500, batagay, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=batagay
    315 of 500, thompson, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=thompson
    316 of 500, victoria, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=victoria
    Complete
    318 of 500, hofn, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hofn
    319 of 500, vardo, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=vardo
    320 of 500, busselton, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=busselton
    321 of 500, busselton, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=busselton
    Complete
    323 of 500, jamestown, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=jamestown
    Complete
    325 of 500, kisangani, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=kisangani
    326 of 500, kapaa, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=kapaa
    327 of 500, solnechnyy, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=solnechnyy
    328 of 500, saint george, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=saint george
    329 of 500, east london, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=east london
    330 of 500, cidreira, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=cidreira
    331 of 500, sola, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=sola
    332 of 500, beyneu, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=beyneu
    333 of 500, thompson, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=thompson
    334 of 500, mareeba, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=mareeba
    335 of 500, togur, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=togur
    336 of 500, barrow, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=barrow
    337 of 500, yellowknife, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=yellowknife
    338 of 500, kodiak, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=kodiak
    339 of 500, tiksi, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=tiksi
    340 of 500, tarko-sale, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=tarko-sale
    341 of 500, castro, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=castro
    342 of 500, busselton, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=busselton
    343 of 500, umba, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=umba
    Complete
    345 of 500, jacareacanga, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=jacareacanga
    346 of 500, alugan, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=alugan
    347 of 500, ushuaia, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=ushuaia
    348 of 500, thompson, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=thompson
    349 of 500, vila, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=vila
    350 of 500, rabo de peixe, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=rabo de peixe
    351 of 500, rikitea, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=rikitea
    352 of 500, ust-ilimsk, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=ust-ilimsk
    353 of 500, talnakh, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=talnakh
    354 of 500, mar del plata, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=mar del plata
    355 of 500, albany, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=albany
    356 of 500, orebro, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=orebro
    357 of 500, te anau, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=te anau
    358 of 500, qaanaaq, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=qaanaaq
    359 of 500, laguna, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=laguna
    360 of 500, kondinskoye, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=kondinskoye
    361 of 500, dickinson, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=dickinson
    362 of 500, outlook, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=outlook
    Complete
    364 of 500, vaini, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=vaini
    365 of 500, ushuaia, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=ushuaia
    366 of 500, chuy, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=chuy
    367 of 500, hobart, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hobart
    368 of 500, lafiagi, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=lafiagi
    Complete
    370 of 500, hermanus, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hermanus
    371 of 500, simoes, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=simoes
    Complete
    373 of 500, qaanaaq, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=qaanaaq
    374 of 500, dingli, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=dingli
    375 of 500, dikson, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=dikson
    376 of 500, new norfolk, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=new norfolk
    377 of 500, hilo, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hilo
    Complete
    379 of 500, thompson, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=thompson
    380 of 500, rikitea, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=rikitea
    381 of 500, katsuura, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=katsuura
    382 of 500, hermanus, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hermanus
    383 of 500, kavaratti, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=kavaratti
    Complete
    385 of 500, albany, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=albany
    386 of 500, soc trang, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=soc trang
    387 of 500, tual, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=tual
    388 of 500, provideniya, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=provideniya
    389 of 500, tarrafal, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=tarrafal
    390 of 500, east london, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=east london
    391 of 500, carnarvon, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=carnarvon
    392 of 500, punta arenas, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=punta arenas
    393 of 500, hobart, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hobart
    394 of 500, naze, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=naze
    395 of 500, tuktoyaktuk, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=tuktoyaktuk
    396 of 500, shache, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=shache
    397 of 500, busselton, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=busselton
    398 of 500, lupeni, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=lupeni
    Complete
    400 of 500, georgetown, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=georgetown
    401 of 500, east london, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=east london
    402 of 500, cavalcante, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=cavalcante
    403 of 500, port alfred, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=port alfred
    404 of 500, cuxhaven, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=cuxhaven
    405 of 500, qaanaaq, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=qaanaaq
    406 of 500, arraial do cabo, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=arraial do cabo
    Complete
    408 of 500, leningradskiy, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=leningradskiy
    409 of 500, vaini, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=vaini
    410 of 500, komsomolskiy, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=komsomolskiy
    411 of 500, biasca, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=biasca
    Complete
    413 of 500, maniitsoq, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=maniitsoq
    414 of 500, mahebourg, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=mahebourg
    415 of 500, busselton, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=busselton
    416 of 500, geraldton, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=geraldton
    417 of 500, bandarbeyla, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bandarbeyla
    418 of 500, saldanha, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=saldanha
    419 of 500, paamiut, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=paamiut
    Complete
    Complete
    422 of 500, castro, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=castro
    423 of 500, ponta do sol, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=ponta do sol
    424 of 500, ushuaia, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=ushuaia
    425 of 500, ilulissat, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=ilulissat
    426 of 500, hirado, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hirado
    427 of 500, rikitea, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=rikitea
    428 of 500, geraldton, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=geraldton
    429 of 500, artyom, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=artyom
    430 of 500, pangnirtung, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=pangnirtung
    431 of 500, feldru, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=feldru
    Complete
    Complete
    434 of 500, chuy, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=chuy
    435 of 500, pacific grove, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=pacific grove
    436 of 500, kahului, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=kahului
    437 of 500, bredasdorp, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bredasdorp
    438 of 500, norman wells, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=norman wells
    439 of 500, port alfred, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=port alfred
    440 of 500, tiksi, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=tiksi
    441 of 500, tuktoyaktuk, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=tuktoyaktuk
    442 of 500, tilichiki, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=tilichiki
    443 of 500, hilo, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hilo
    444 of 500, carnarvon, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=carnarvon
    445 of 500, pisco, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=pisco
    446 of 500, rikitea, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=rikitea
    447 of 500, butaritari, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=butaritari
    448 of 500, hobart, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hobart
    449 of 500, atuona, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=atuona
    450 of 500, severo-kurilsk, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=severo-kurilsk
    451 of 500, new norfolk, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=new norfolk
    452 of 500, nuuk, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=nuuk
    453 of 500, waltershausen, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=waltershausen
    454 of 500, ballina, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=ballina
    Complete
    456 of 500, new norfolk, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=new norfolk
    457 of 500, deputatskiy, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=deputatskiy
    458 of 500, mabay, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=mabay
    459 of 500, busselton, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=busselton
    460 of 500, iqaluit, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=iqaluit
    461 of 500, beinamar, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=beinamar
    462 of 500, hobart, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hobart
    463 of 500, narsaq, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=narsaq
    Complete
    465 of 500, catuday, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=catuday
    Complete
    467 of 500, hermanus, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=hermanus
    468 of 500, flinders, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=flinders
    469 of 500, namatanai, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=namatanai
    470 of 500, rikitea, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=rikitea
    Complete
    472 of 500, atar, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=atar
    473 of 500, jamestown, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=jamestown
    474 of 500, isangel, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=isangel
    475 of 500, jamestown, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=jamestown
    476 of 500, rikitea, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=rikitea
    477 of 500, bubaque, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bubaque
    Complete
    Complete
    480 of 500, punta arenas, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=punta arenas
    481 of 500, leningradskiy, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=leningradskiy
    482 of 500, bredasdorp, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bredasdorp
    483 of 500, saint-philippe, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=saint-philippe
    Complete
    485 of 500, bagdarin, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=bagdarin
    Complete
    487 of 500, tuatapere, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=tuatapere
    Complete
    Complete
    Complete
    491 of 500, arraial do cabo, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=arraial do cabo
    492 of 500, alice springs, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=alice springs
    493 of 500, haines junction, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=haines junction
    Complete
    495 of 500, tuatapere, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=tuatapere
    Complete
    497 of 500, punta arenas, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=punta arenas
    498 of 500, dunedin, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=dunedin
    499 of 500, husavik, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=husavik
    500 of 500, rikitea, http://api.openweathermap.org/data/2.5/weather?appid=d9f788ccd230de9dfedc79a53db72d7f&unitsimperial&q=rikitea



```python
df = (pd.DataFrame([ x.split(', ') for x in weather_csv]))
df.columns = ["Count","City","URL"]
df.to_csv('Weather.csv', index=False)
```


```python
summary = ["name", "main.temp_max","main.humidity","wind.speed","clouds.all","coord.lat"]
data =[response(*summary) for response in weather_data]

columnnames = ["City","Max Temp","Humidity","Wind Speed","Cloudiness","Latitude"]
data =pd.DataFrame(data,columns = columnnames)
data.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>City</th>
      <th>Max Temp</th>
      <th>Humidity</th>
      <th>Wind Speed</th>
      <th>Cloudiness</th>
      <th>Latitude</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Bathsheba</td>
      <td>78.80</td>
      <td>78</td>
      <td>17.22</td>
      <td>40</td>
      <td>13.22</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Bathsheba</td>
      <td>78.80</td>
      <td>78</td>
      <td>17.22</td>
      <td>40</td>
      <td>13.22</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Hobart</td>
      <td>73.40</td>
      <td>35</td>
      <td>19.46</td>
      <td>0</td>
      <td>-42.88</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Atuona</td>
      <td>79.89</td>
      <td>100</td>
      <td>13.47</td>
      <td>24</td>
      <td>-9.80</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Ippy</td>
      <td>71.79</td>
      <td>64</td>
      <td>8.43</td>
      <td>8</td>
      <td>6.27</td>
    </tr>
  </tbody>
</table>
</div>



# Latitude vs Temperature Plot


```python
# Set style of scatterplot
xaxis = data['Latitude']
yaxis = data['Max Temp']
sns.set()
sns.regplot(x=xaxis, y=yaxis, marker="o", fit_reg=False)
plt.title('City Latitude vs Max Temperature')
plt.xlabel('Latitude')
plt.ylabel('Max Temp (F)')
plt.savefig('Temp_vs_Lat')
plt.show()
```


![png](output_9_0.png)


# Latitude vs. Humidity Plot


```python
xaxis = data['Latitude']
yaxis = data['Humidity']
sns.set()
sns.regplot(x=xaxis, y=yaxis, marker="o", fit_reg=False)
plt.title('City Latitude vs Humidity')
plt.xlabel('Latitude')
plt.ylabel('Humidity(%)')
plt.savefig('Humidity_vs_Lat')
plt.show()
```


![png](output_11_0.png)


# Latitude vs. Cloudiness Plot


```python
xaxis = data['Latitude']
yaxis = data['Cloudiness']
sns.set()
sns.regplot(x=xaxis, y=yaxis, marker="o", fit_reg=False)
plt.title('City Latitude vs Cloudiness')
plt.xlabel('Latitude')
plt.ylabel('Cloud Cover(%)')
plt.savefig('Cloud_vs_Lat')
plt.show()
```


![png](output_13_0.png)


# Latitude vs. Wind Speed Plot


```python
xaxis = data['Latitude']
yaxis = data['Wind Speed']
sns.set()
sns.regplot(x=xaxis, y=yaxis, marker="o", fit_reg=False)
plt.title('City Latitude vs Wind Speed')
plt.xlabel('Latitude')
plt.ylabel('Wind Speed (mph)')
plt.savefig('Wind_vs_Lat')
plt.show()
```


![png](output_15_0.png)

