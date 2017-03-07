#Места

[Глвня](https://github.com/tolyaganzin/skyscanner-RU) [<-База](https://github.com/tolyaganzin/skyscanner-RU/blob/master/base.md) | [Отели->](https://github.com/tolyaganzin/skyscanner-RU/blob/master/hotels/hotels.md)

* Places [офф документация](https://skyscanner.github.io/slate/#places)
* Примичание **{country}/{currency}/{locale}** [смотри здесь](https://github.com/tolyaganzin/skyscanner-RU/blob/master/base.md)

--------------------------------------------------------------------------------------

* Получение списка всех мест (подробность ограничена до города), которые поддерживает апиха
* Получает список мест по строке запроса
* Получает информацию про: страну, город или аеропорт - используя их ID
* Аренда авто и номеров отелей


##Cписка всех мест (запрос типа GET)

Синтаксис
```
http://partners.api.skyscanner.net/apiservices/
    geo/v1.0?
    apiKey={apiKey}
```

Пример
```
http://partners.api.skyscanner.net/apiservices
    /geo/v1.0?
    apikey=prtl6749387986743898559646983194
```

Результат
```json
{
  "Continents": [
    {
      "Countries": [
        {
          "CurrencyId": "AFN",
          "Regions": [],
          "Cities": [
            {
              "SingleAirportCity": true,
              "Airports": [
                {
                  "CityId": "BINA",
                  "CountryId": "AF",
                  "Location": "67.823611, 34.804167",
                  "Id": "BIN",
                  "Name": "Bamiyan"
                }
              ],
              "CountryId": "AF",
              "Location": "67.823611, 34.804167",
              "IataCode": "BIN",
              "Id": "BINA",
              "Name": "Bamiyan"
            },
            ...
          ],
          "Id": "AF",
          "Name": "Afghanistan"
        },
        ...
      ],
      "Id": "A",
      "Name": "Asia"
    },
    ...
  ]
 }
```
###[Подробнее](https://github.com/tolyaganzin/skyscanner-RU/blob/master/places/details/geo.md)


##Cписок мест по строке запроса (запрос типа GET)


Синтаксис
```
http://partners.api.skyscanner.net/apiservices/
    autosuggest/v1.0/{country}/{currency}/{locale}?
    query={query}&
    apiKey={apiKey}
```

Пример
```
http://partners.api.skyscanner.net/apiservices/
    autosuggest/v1.0/UK/GBP/en-GB?
    query=pari&
    apiKey=prtl6749387986743898559646983194
```

Результат
```json
{
  "Places": [
    {
      "PlaceId": "PARI-sky",
      "PlaceName": "Paris",
      "CountryId": "FR-sky",
      "RegionId": "",
      "CityId": "PARI-sky",
      "CountryName": "France"
    },
    {
      "PlaceId": "CDG-sky",
      "PlaceName": "Paris Charles de Gaulle",
      "CountryId": "FR-sky",
      "RegionId": "",
      "CityId": "PARI-sky",
      "CountryName": "France"
    },
    {
      "PlaceId": "ORY-sky",
      "PlaceName": "Paris Orly",
      "CountryId": "FR-sky",
      "RegionId": "",
      "CityId": "PARI-sky",
      "CountryName": "France"
    },
  ...
  ]
}
```
[подробнее](https://github.com/tolyaganzin/skyscanner-RU/blob/master/places/details/placesList.md)


##Информацию про: страну, город или аеропорт (запрос типа GET)

Синтаксис
```
http://partners.api.skyscanner.net/apiservices/
    autosuggest/v1.0/{market}/{currency}/{locale}?
    id={place_id}&
    apiKey={apiKey}
```

Пример
```
http://partners.api.skyscanner.net/apiservices/
    autosuggest/v1.0/UK/GBP/en-GB?
    id=pari&
    apiKey=prtl6749387986743898559646983194
```

Результат
```json
{
  "Places": [
    {
      "PlaceId": "PARI-sky",
      "PlaceName": "Paris",
      "CountryId": "FR-sky",
      "CityId": "PARI-sky",
      "CountryName": "France"
    }
  ]
}
```


##Аренда авто и номеров отелей (запрос типа GET)
###{query} - то что мы ищем

Синтаксис
```
http://partners.api.skyscanner.net/hotels/autosuggest/v2/
    {country}/{currency}/{locale}/
    {query}?
    apiKey={apiKey}
```

Пример
```
http://partners.api.skyscanner.net/apiservices/hotels/autosuggest/v2/
    UA/USD/ru-RU/
    zaporizhya?
    apikey=prtl6749387986743898559646983194
```

Результат
```json
{
  "places": [
    {
      "place_id": 1,
      "admin_level1": "Запорожская область",
      "country_name": "Украина"
    },
    {
      "place_id": 2,
      "city_name": "Zaporizhia",
      "admin_level1": "Запорожская область",
      "country_name": "Украина"
    },
    {
      "place_id": 3,
      "country_name": "Украина"
    }
  ],
  "results": [
    {
      "display_name": "Zaporizhia",
      "parent_place_id": 1,
      "individual_id": "44896770",
      "geo_type": "City",
      "localised_geo_type": "Город",
      "is_bookable": false
    },
    {
      "display_name": "Zaporizhia (OZH)",
      "parent_place_id": 2,
      "individual_id": "114117160",
      "geo_type": "Airport",
      "localised_geo_type": "Аэропорт",
      "is_bookable": false
    },
    {
      "display_name": "Apartments",
      "parent_place_id": 2,
      "individual_id": "47179991",
      "geo_type": "Apartment",
      "localised_geo_type": "Апартаменты",
      "is_bookable": true
    },
    {
      "display_name": "Lenina Avenue",
      "parent_place_id": 2,
      "individual_id": "102962720",
      "geo_type": "Transitway",
      "localised_geo_type": "Улица",
      "is_bookable": false
    },
    {
      "display_name": "Zaporizhia Oblast",
      "parent_place_id": 3,
      "individual_id": "44291765",
      "geo_type": "FirstLevelNationAdministrativeDivision",
      "localised_geo_type": "Регион",
      "is_bookable": false
    },
    {
      "display_name": "Славутич-Арена",
      "parent_place_id": 2,
      "individual_id": "114133024",
      "geo_type": "Stadium",
      "localised_geo_type": "Стадион",
      "is_bookable": false
    },
    {
      "display_name": "Reikartz Zaporizhia",
      "parent_place_id": 2,
      "individual_id": "56665948",
      "geo_type": "Hotel",
      "localised_geo_type": "Отель",
      "is_bookable": true
    },
    ...
  ]
}
```
