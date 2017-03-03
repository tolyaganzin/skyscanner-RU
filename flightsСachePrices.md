#Инфрмация о возможных полетах

[Глвня](https://github.com/tolyaganzin/skyscanner-RU) [<-Аренда авто](https://github.com/tolyaganzin/skyscanner-RU/blob/master/carHire.md)

* Обзор направлений [офф документация](https://skyscanner.github.io/slate/#browse-quotes)
* Обзор дат [офф документация](https://skyscanner.github.io/slate/#browse-dates)

**Остальные 2 запроса выдают какое-то дерьмо**

##Обзор направлений (запрос типа GET)

Синтаксис
```
//Запрос
http://partners.api.skyscanner.net/apiservices/browsequotes/v1.0/
    {country}/{currency}/{locale}/
    {originPlace}/{destinationPlace}/
    {outboundPartialDate}/{inboundPartialDate}?
    apiKey={apiKey}
//Заголовок  
  Accept: application/json
```

Пример
```
http://partners.api.skyscanner.net/apiservices/browsequotes/v1.0/
    UA/UAH/ru-RU/
    ODS/IEV/
    2017-05-01/2017-05-07?
    apikey=prtl6749387986743898559646983194
```

Результат
```json
{
  "Quotes": [],
  "Places": [
    {
      "PlaceId": 58646,
      "IataCode": "IEV",
      "Name": "Жуляны (Киев)",
      "Type": "Station",
      "SkyscannerCode": "IEV",
      "CityName": "Киев",
      "CityId": "KIEV",
      "CountryName": "Украина"
    },
    {
      "PlaceId": 72419,
      "IataCode": "ODS",
      "Name": "Одесса",
      "Type": "Station",
      "SkyscannerCode": "ODS",
      "CityName": "Одесса",
      "CityId": "ODES",
      "CountryName": "Украина"
    }
  ],
  "Carriers": [
    {
      "CarrierId": 1401,
      "Name": "Motor Sich Airlines"
    }
  ],
  "Currencies": [
    {
      "Code": "UAH",
      "Symbol": "грн.",
      "ThousandsSeparator": " ",
      "DecimalSeparator": ",",
      "SymbolOnLeft": false,
      "SpaceBetweenAmountAndSymbol": false,
      "RoundingCoefficient": 0,
      "DecimalDigits": 2
    }
  ]
}
```


##Обзор дат (запрос типа GET)

Синтаксис
```
//Запрос
http://partners.api.skyscanner.net/apiservices/browsedates/v1.0/
    {country}/{currency}/{locale}/
    {originPlace}/{destinationPlace}/
    {outboundPartialDate}/{inboundPartialDate}?
    apiKey={apiKey}
//Заголовок  
  Accept: application/json
```

Пример
```
http://partners.api.skyscanner.net/apiservices/browsedates/v1.0/
    UA/UAH/ru-RU/
    ODS/IEV/
    2017-05/2017-05?
    apikey=prtl6749387986743898559646983194
```

Результат
```json
"Dates": {
    "OutboundDates": [
      {
        "PartialDate": "2017-05-01",
        "QuoteIds": [
          1,
          2,
          3
        ],
        "Price": 2239,
        "QuoteDateTime": "2017-02-20T20:04:00"
      },
      {
        "PartialDate": "2017-05-04",
        "QuoteIds": [
          4
        ],
        "Price": 2371,
        "QuoteDateTime": "2017-03-01T18:43:00"
      },
      ...
    ],
    "InboundDates": [
      {
        "PartialDate": "2017-05-05",
        "QuoteIds": [
          1
        ],
        "Price": 2384,
        "QuoteDateTime": "2017-03-01T19:20:00"
      },
      ...
    ]
  },
  "Quotes": [
    {
      "QuoteId": 1,
      "MinPrice": 2384,
      "Direct": true,
      "OutboundLeg": {
        "CarrierIds": [
          1401
        ],
        "OriginId": 72419,
        "DestinationId": 58646,
        "DepartureDate": "2017-05-01T00:00:00"
      },
      "InboundLeg": {
        "CarrierIds": [
          1401
        ],
        "OriginId": 58646,
        "DestinationId": 72419,
        "DepartureDate": "2017-05-05T00:00:00"
      },
      "QuoteDateTime": "2017-03-01T19:20:00"
    },
    ...
  ],
  "Places": [
    {
      "PlaceId": 58646,
      "IataCode": "IEV",
      "Name": "Жуляны (Киев)",
      "Type": "Station",
      "SkyscannerCode": "IEV",
      "CityName": "Киев",
      "CityId": "KIEV",
      "CountryName": "Украина"
    },
    {
      "PlaceId": 72419,
      "IataCode": "ODS",
      "Name": "Одесса",
      "Type": "Station",
      "SkyscannerCode": "ODS",
      "CityName": "Одесса",
      "CityId": "ODES",
      "CountryName": "Украина"
    }
  ],
  "Carriers": [
    {
      "CarrierId": 1401,
      "Name": "Motor Sich Airlines"
    }
  ],
  "Currencies": [
    {
      "Code": "UAH",
      "Symbol": "грн.",
      "ThousandsSeparator": " ",
      "DecimalSeparator": ",",
      "SymbolOnLeft": false,
      "SpaceBetweenAmountAndSymbol": false,
      "RoundingCoefficient": 0,
      "DecimalDigits": 2
    }
  ]
}
```
