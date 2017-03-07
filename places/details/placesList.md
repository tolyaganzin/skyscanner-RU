#Cписок мест по строке запроса (ответ)

###Places

* PlaceId - уникальный ключь места который был описан в запросе рание
* PlaceName - название места
* CountryId - уникальный страны места который был описан в запросе рание
* RegionId - уникальный региона места который был описан в запросе рание (он приходит постоянно пустой)
* CityId - уникальный города места который был описан в запросе рание
* CountryName - название страны

###Запрос кторый описывает пункты списка выше [подробнее](https://github.com/tolyaganzin/skyscanner-RU/blob/master/places/details/geo.md)

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
    ...
  ]
}
```
