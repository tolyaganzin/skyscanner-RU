#Места

[Глвня](https://github.com/tolyaganzin/skyscanner-RU) [<-База](https://github.com/tolyaganzin/skyscanner-RU/blob/master/base.md) | [Отели->](https://github.com/tolyaganzin/skyscanner-RU/blob/master/hotels/hotels.md)

* Places [офф документация](https://skyscanner.github.io/slate/#places)
* Примичание **{country}/{currency}/{locale}** [смотри здесь](https://github.com/tolyaganzin/skyscanner-RU/blob/master/base.md)

--------------------------------------------------------------------------------------

* Получение списка всех мест, которые поддерживает апиха
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
http://partners.api.skyscanner.net/hotels/autosuggest/v2/{country}/{currency}/{locale}/{query}?
    apiKey={apiKey}
```

Пример
```
http://partners.api.skyscanner.net/apiservices/hotels/autosuggest/v2/UA/USD/ru-RU/pari?
    apikey=prtl6749387986743898559646983194
```

Результат
```json
{
  "places": [
    {
      "place_id": 1,
      "city_name": "Paris",
      "admin_level1": "Île-de-France",
      "country_name": "France"
    },
    {
      "place_id": 2,
      "admin_level1": "Île-de-France",
      "country_name": "France"
    },
  ...
  ],
  "results": [
    {
      "display_name": "Paris",
      "parent_place_id": 1,
      "individual_id": "27539733",
      "geo_type": "City",
      "localised_geo_type": "City",
      "is_bookable": false
    },
    {
      "display_name": "Paris 08 Élysée",
      "parent_place_id": 1,
      "individual_id": "27562771",
      "geo_type": "District",
      "localised_geo_type": "District",
      "is_bookable": false
    },
    ...
  ]
}
```
