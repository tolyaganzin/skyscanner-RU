
#Отели

* Places [офф документация](https://skyscanner.github.io/slate/#places)
* Hotels Price List and Hotels Details service [офф документация](https://support.business.skyscanner.net/hc/en-us/articles/212098705-Hotels-Price-List-and-Hotels-Details-service#createdetails)

[Глвня](https://github.com/tolyaganzin/skyscanner-RU) [База](https://github.com/tolyaganzin/skyscanner-RU/blob/master/base.md)

* Получение всех мест из запроса
* Получение уникального идинтификатора места (отеля)
* Подробная информация об отеле


##Получает все места по их совпадению с запросом


Синтаксис
```
http://partners.api.skyscanner.net/apiservices/hotels/autosuggest/v2/
    {market}/
    {currency}/
    {locale}/
    {query}?
    apikey={apikey}
```

###Примеры:

Пример - 1
Данный запрос получил все места находящиеся в городе: Запорожье
```
http://partners.api.skyscanner.net/apiservices/hotels/autosuggest/v2/
    UA/
    USD/
    ru-RU/
    zaporizhya?
    apikey=prtl6749387986743898559646983194
```

Пример - 2
```
http://partners.api.skyscanner.net/apiservices/hotels/autosuggest/v2/
    UA/
    USD/
    ru-RU/
    ukraine?apikey=prtl6749387986743898559646983194
```

Выведет масивы: мест и результатов. В масиве результатов указаныны: город, апартаменты, аэропорт, стадион, улицы, отели (указываеться в поле geo_type).
В местах ВАЖНО СМОТРЕТЬ на наличиие поля country_name, если это касаеться конкретной страны, а так же поле city_name, если нужен конкретный город. При поиске в масиве результатов поле parent_place_id должно соответствовать полю place_id в масиве мест.


##Получение отелей и цен по идентификатору individual_id из результата запроса выше
```
entityid = individual_id
```
Синтаксис
```
http://partners.api.skyscanner.net/apiservices/hotels/liveprices/v2/
    {market}/
    {currency}/
    {locale}/
    {entityid}/
    {checkindate}/
    {checkoutdate}/
    {guests}/
    {rooms}?
    apiKey={apiKey}
    [&pageSize={pageSize}]
```

Пример
```
http://partners.api.skyscanner.net/apiservices/hotels/liveprices/v2/
    UA/
    USD/
    ru-RU/
    114449549/
    2017-05-04/
    2017-05-10/
    2/
    1?
    apiKey=prtl6749387986743898559646983194
```

##Получение подробной информации об отеле

Синтаксис
```
http://partners.api.skyscanner.net/apiservices/hotels/livedetails/v2/details/
    {session key}?
    apiKey={encryptedApiKey}
    &hotelIds={hotelIds}
```

###Получение ключей
```
{session key} и {encryptedApiKey} мы получаем из запроса выше из объекта "urls" поля "hotel_details"
{hotelIds} мы берем из объекта "hotels" поля "hotel_id" (hotel_id соответствует объекта "hotels_prices" полю id) - передать можно лишь 1 id
```

Схема сборки запроса
```
"http://partners.api.skyscanner.net" + urls.hotel_details + hotels_prices.id
```

Пример
```
http://partners.api.skyscanner.net/apiservices/hotels/livedetails/v2/details/
    H4sIAAAAAAAEAKtWyleyilYKdVTSUSoq1Q0KBdKhwS5A0tDQxMTE0tTEEsg2MjA01zUw1TUwCTEwsAIjJFFDAyRRIx1DoF5jHSMgw9RQSSevNCcnVkcpT8lK19LcxLgWAGUE2ARxAAAA0?
    apikey=_wVpmI14SOFx5TVFMGIRHygS6xZQksyyo6gF0HIdhepkbgUoByWEBEMEqpXrMC4lKVbqL6eB7oqsknxsI3bc67g%3D%3D
    &hotelIds=95823343
```

###Уточнение
* {session key} и {encryptedApiKey} - действуют достаточно не долго (примерно 12 часов)
* Если в поле **hotelIds** нужно передать более одного параметра - их нужно разделить запятой.
```
hotelIds=95823343,46999735,56665948
```
Но при ответе мы получим пустой масив **hotels_prices**, а остальные данные дополняться в соответствии с запросом. Это не страшно так как цены отелей были в запросе выше.
