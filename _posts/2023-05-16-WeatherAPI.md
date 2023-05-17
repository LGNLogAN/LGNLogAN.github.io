---
layout: single
title:  "Python을 활용한 패스워드 설정 프로그램"
---

# OpenWeatherMap API를 이용한 날씨 정보를 얻기

```python
import requests
import json
import time

city = 'Seoul' #도시
apiKey = "481b307882ce8a4efb0cf18ecb73f6dd"
lang = 'kr' #언어
units = 'metric' #화씨 온도를 섭씨 온도로 변경
api = f"https://api.openweathermap.org/data/2.5/weather?q={city}&appid={apiKey}&lang={lang}&units={units}"

result = requests.get(api)
result = json.loads(result.text)


name = result['name']
lon = result['coord']['lon']
lat = result['coord']['lat']
weather = result['weather'][0]['main']
temperature = result['main']['temp']
humidity = result['main']['humidity']


if name == 'Seoul':
    name = '서울'

if weather == 'Clouds':
    weather = '구름조금'
elif weather == 'Clear':
    weather = '맑음'
elif weather == 'Rain':
    weather = '비'
    
current_time = time.localtime()  # 현재 시간을 지역 시간대에 맞게 반환
formatted_time = time.strftime("%Y년%m월%d일 %H:%M:%S", current_time)  # 형식에 맞게 시간을 문자열로 변환

print(formatted_time)
print(name) #지역명
print(weather) #날씨
print(str(int(temperature))+'℃') #온도
# print(humidity) #습기

```
# 결과
<pre>
2023년05월17일 15:27:37
서울
맑음
27℃
</pre>
