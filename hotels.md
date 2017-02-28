#Получает все места по их совпадению с запросом

##Синтаксис
http://partners.api.skyscanner.net/apiservices/hotels/autosuggest/v2/{market}/{currency}/{locale}/{query}?apikey={apikey}

##Примеры:
###Пример - 1
Данный запрос получил все места находящиеся в городе: Запорожье
```
http://partners.api.skyscanner.net/apiservices/hotels/autosuggest/v2/UA/USD/ru-RU/zaporizhya?apikey=prtl6749387986743898559646983194
```

###Пример - 2
```
http://partners.api.skyscanner.net/apiservices/hotels/autosuggest/v2/UA/USD/ru-RU/ukraine?apikey=prtl6749387986743898559646983194
```

Выведет масивы: мест и результатов. В масиве результатов указаныны: город, апартаменты, аэропорт, стадион, улицы, отели. (указываеться в поле geo_type)
В местах ВАЖНО СМОТРЕТЬ на наличиие поля country_name, если это касаеться конкретной страны, а так же поле city_name, если нужен конкретный город. При поиске в масиве результатов поле parent_place_id должно соответствовать полю place_id в масиве мест.

--------------------------------------------------------------------------------
#Получение отелей и цен по идентификатору individual_id из результата запроса выше
```
entityid = individual_id
```
##Синтаксис
```
http://partners.api.skyscanner.net/apiservices/hotels/liveprices/v2/{market}/{currency}/{locale}/{entityid}/{checkindate}/{checkoutdate}/{guests}/{rooms}?apiKey={apiKey}[&pageSize={pageSize}]
```

##Пример
```
http://partners.api.skyscanner.net/apiservices/hotels/liveprices/v2/UA/USD/ru-RU/114449549/2017-05-04/2017-05-10/2/1?apiKey=prtl6749387986743898559646983194
```
--------------------------------------------------------------------------------
#Получение подробной информации об отеле

##Синтаксис
```
http://partners.api.skyscanner.net/apiservices/hotels/livedetails/v2/details/{session key}?apiKey={encryptedApiKey}&hotelIds={hotelIds}
```
###Получение ключей
```
{session key} и {encryptedApiKey} мы получаем из запроса выше из объекта "urls" поля "hotel_details"
{hotelIds} мы берем из объекта "hotels" поля "hotel_id" (hotel_id соответствует объекта "hotels_prices" полю id) - передать можно лишь 1 id
```
###Схема сборки запроса
```
"http://partners.api.skyscanner.net" + urls.hotel_details + hotels_prices.id
```
##Пример

Пример схемы сборки
```
http://partners.api.skyscanner.net
```
+
```
/apiservices/hotels/livedetails/v2/details/H4sIAAAAAAAEAKtWyleyilYKdVTSUSoq1Q0KBdKhwS5A0tDQxMTE0tTEEsg2MjA01zUw1TUwCTEwsAIjJFFDAyRRIx1DoF5jHSMgw9RQSSevNCcnVkcpT8lK19LcxLgWAGUE2ARxAAAA0?apikey=_wVpmI14SOFx5TVFMGIRHygS6xZQksyyo6gF0HIdhepkbgUoByWEBEMEqpXrMC4lKVbqL6eB7oqsknxsI3bc67g%3D%3D
```
+
```
&hotelIds=95823343
```
###Готовый запрос
```
http://partners.api.skyscanner.net/apiservices/hotels/livedetails/v2/details/H4sIAAAAAAAEAKtWyleyilYKdVTSUSoq1Q0KBdKhwS5A0tDQxMTE0tTEEsg2MjA01zUw1TUwCTEwsAIjJFFDAyRRIx1DoF5jHSMgw9RQSSevNCcnVkcpT8lK19LcxLgWAGUE2ARxAAAA0?apikey=_wVpmI14SOFx5TVFMGIRHygS6xZQksyyo6gF0HIdhepkbgUoByWEBEMEqpXrMC4lKVbqL6eB7oqsknxsI3bc67g%3D%3D&hotelIds=95823343
```
