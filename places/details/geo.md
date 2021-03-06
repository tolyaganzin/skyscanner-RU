#Подробно об ответе на запрос списка всех поддерживаемых мест

[Глвня](https://github.com/tolyaganzin/skyscanner-RU) / [Места](https://github.com/tolyaganzin/skyscanner-RU/blob/master/places/places.md)

* Continents	- содержит список(масив) с объектами типа "Continent" [подробнее](#continents)
* Countries	- содержит список(масив) со всеми странами [подробнее](#countries)
* Cities - содержит список(масив) со всеми городами [подробнее](#cities)
* Airports содержит список(масив) со всеми аеропортами в городе, если они имеються [подробнее](#airports)


##Continents

* Id - уникальный ключь, может быть лишь один символ (A, C, E, F, I, M, N, O, S, X, Y, Z)
* Name - имя континента или части мира
* Countries - масив объектов стран принадлежащих к текущему континенту

```json
"Continents": [
    {
      "Countries": [...],
      "Id": "A",
      "Name": "Asia"
    },
    ...
]
```


##Countries

* Id - уникальный ключь, может быть лишь два символа
* Name - название страны
* CurrencyId - уникальный ключь валюты. Всегда состоит из трех символов
* Cities - города текущей страны
* Regions - может быть пустым, включает в себя объекты-регионы страны если таковые есть
* LanguageId - идентификатор языка. Может отсутствовать, если масив регионов пуст

```json
"Countries": [
  {
    "CurrencyId": "AFN",
    "Regions": [],
    "Cities": [...],
    "Id": "AF",
    "Name": "Afghanistan"    
  },
  ...
]
```

##Cities

* SingleAirportCity - логическое поле наличия в городе одного аеропорта или более
* Airports - масив аеропортов
* CountryId - уникальный идетификатор страны родителя по отношению к городу (описан выше)
* Location - широта и долгота расположения города
* IataCode - уникальный код города который всегда состоит из трех символов и нужен для запросов связанных с арендой авто и перелетами
* Id - уникальный код города как правило состоит из четырех символов
* Name - имя города

```json
"Cities": [
  {
    "SingleAirportCity": true,
    "Airports": [...],
    "CountryId": "AF",
    "Location": "67.823611, 34.804167",
    "IataCode": "BIN",
    "Id": "BINA",
    "Name": "Bamiyan"
  },
  ...
],
```

##Airports

* CityId - ключь города в котором аеропорт находиться
* CountryId - ключь страны в которой данный город расположен
* Location - широта и долгота расположения аеропорта
* Id - уникальный идентификатор аеропорта
* Name - название аеропорта

```json
"Airports": [
  {
    "CityId": "BINA",
    "CountryId": "AF",
    "Location": "67.823611, 34.804167",
    "Id": "BIN",
    "Name": "Bamiyan"
  },
  ...
],
```
