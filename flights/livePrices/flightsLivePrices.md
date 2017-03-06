#Цены на перелеты

[Глвня](https://github.com/tolyaganzin/skyscanner-RU) / [Перелеты](https://github.com/tolyaganzin/skyscanner-RU/blob/master/flights/flights.md)

* Places [офф документация](https://skyscanner.github.io/slate/#places)
* Flights Live Prices [офф документация](https://skyscanner.github.io/slate/#flights-live-prices)

------------------------------------------------------------------------------------------

* Создание сессии
* Получение данных сессии
* Получение данных деталей сессии


##Создание сессии (запрос типа POST)

Пример
```
//Запрос
http://partners.api.skyscanner.net/apiservices/pricing/v1.0
//Загоровки
    Content-Type: application/x-www-form-urlencoded
    [X-Forwarded-For: 127.0.0.1]
    [Accept: application/json]
//Тело запроса
    country:UA
    currency:UAH
    locale:ru-RU
    locationSchema:iata
    originplace:ODS
    destinationplace:IEV
    outbounddate:2017-05-01
    inbounddate:2017-05-07
    adults:1
    children:0
    infants:0
    apikey:prtl6749387986743898559646983194
```
Результат
```
//Заголовки
Cache-Control →private
Content-Length →2
Content-Type →application/json
Date →Fri, 03 Mar 2017 10:07:11 GMT
Location →http://partners.api.skyscanner.net/apiservices/pricing/uk1/v1.0/d9117ab4018c4626afb80083d64ee742_rrsqbjcb_06a13f0a788e803fcc56e78802891a26
```
* Данный запрос на авторизацию может глючить и по этому отправлять его желательно 3-5 раз
* Нам нужна ссылка из **Location** для следующего запроса



##Получение данных сессии (запрос типа GET)
В данном примере **{SessionKey} = d9117ab4018c4626afb80083d64ee742_rrsqbjcb_06a13f0a788e803fcc56e78802891a26**

Синтаксис
```
http://partners.api.skyscanner.net/apiservices/pricing/uk1/v1.0/
    {SessionKey}?
    apiKey={apiKey}
```
Пример
```
http://partners.api.skyscanner.net/apiservices/pricing/uk1/v1.0/
    d9117ab4018c4626afb80083d64ee742_rrsqbjcb_06a13f0a788e803fcc56e78802891a26?
    apikey=prtl6749387986743898559646983194
```
Результат

```json
{
  "SessionKey": "c5bf9d96668a45eb805afa927067c50f_rrsqbjcb_06a13f0a788e803fcc56e78802891a26",
  "Query": {
    "Country": "UA",
    "Currency": "UAH",
    "Locale": "ru-ru",
    "Adults": 1,
    "Children": 0,
    "Infants": 0,
    "OriginPlace": "5819",
    "DestinationPlace": "4110",
    "OutboundDate": "2017-05-01",
    "InboundDate": "2017-05-07",
    "LocationSchema": "Default",
    "CabinClass": "Economy",
    "GroupPricing": false
  },
  "Status": "UpdatesComplete",
  "Itineraries": [
    {
      "OutboundLegId": "14920-1705010740--32042-0-12428-1705010900",
      "InboundLegId": "12428-1705072040--32042-0-14920-1705072200",
      "PricingOptions": [
        {
          "Agents": [
            3513089
          ],
          "QuoteAgeInMinutes": 1,
          "Price": 2231.29,
          "DeeplinkUrl": "http://partners.api.skyscanner.net/apiservices/deeplink/v2?_cje=jzj5DawL5zJyT%2bnfeP9GJWfImnVvZd7vh0AJSObmdOp8YP07VbGmhzc%2bVTc80nUp&url=http%3a%2f%2fwww.apideeplink.com%2ftransport_deeplink%2f4.0%2fUA%2fru-ru%2fUAH%2fotua%2f2%2f14920.12428.2017-05-01%2c12428.14920.2017-05-07%2fair%2ftrava%2fflights%3fitinerary%3dflight%7c-32042%7c253%7c14920%7c2017-05-01T07%3a40%7c12428%7c2017-05-01T09%3a00%2cflight%7c-32042%7c258%7c12428%7c2017-05-07T20%3a40%7c14920%7c2017-05-07T22%3a00%26carriers%3d-32042%26passengers%3d1%26channel%3ddataapi%26cabin_class%3deconomy%26facilitated%3dfalse%26ticket_price%3d2231.29%26is_npt%3dfalse%26is_multipart%3dfalse%26client_id%3dskyscanner_b2b%26request_id%3d20cd20e1-4eab-481a-9f82-68fd7960662d%26deeplink_ids%3deu-central-1.prod_9bd5f84f0d8bb9538d278adf68f3c211%26commercial_filters%3dfalse%26q_datetime_utc%3d2017-03-03T08%3a26%3a22"
        },
        ...
        ],
      "BookingDetailsLink": {
        "Uri": "/apiservices/pricing/v1.0/ab5b948d616e41fb954a4a2f6b8dde1a_ecilpojl_7CAAD17D0CFC34BFDE68DEBFDFD548C7/booking",
        "Body": "OutboundLegId=11235-1705301925--32480-0-13554-1705302055&InboundLegId=13554-1706020700--32480-0-11235-1706020820",
        "Method": "PUT"
      }
    },
    ...
   ],
  "Legs": [
    {
      "Id": "14920-1705010700--31728-0-12911-1705010800",
      "SegmentIds": [
        0
      ],
      "OriginStation": 14920,
      "DestinationStation": 12911,
      "Departure": "2017-05-01T07:00:00",
      "Arrival": "2017-05-01T08:00:00",
      "Duration": 60,
      "JourneyMode": "Flight",
      "Stops": [],
      "Carriers": [
        1571
      ],
      "OperatingCarriers": [
        1571
      ],
      "Directionality": "Outbound",
      "FlightNumbers": [
        {
          "FlightNumber": "56",
          "CarrierId": 1571
        }
      ]
    },
    ...
   ],
   "Segments": [
     {
         "Id": 0,
         "OriginStation": 14920,
         "DestinationStation": 12911,
         "DepartureDateTime": "2017-05-01T07:00:00",
         "ArrivalDateTime": "2017-05-01T08:00:00",
         "Carrier": 1571,
         "OperatingCarrier": 1571,
         "Duration": 60,
         "FlightNumber": "56",
         "JourneyMode": "Flight",
         "Directionality": "Outbound"
      },
      ...
    ],
    "Carriers": [
      {
        "Id": 1571,
        "Code": "PS",
        "Name": "Ukraine International",
        "ImageUrl": "http://s1.apideeplink.com/images/airlines/PS.png",
        "DisplayCode": "PS"
      },
    ...
  ],
  "Agents": [
    {
      "Id": 3289055,
      "Name": "Motor Sich Airlines",
      "ImageUrl": "http://s1.apideeplink.com/images/websites/msi_.png",
      "Status": "UpdatesComplete",
      "OptimisedForMobile": false,
      "Type": "Airline"
    },
    ...
  ],
  "Places": [
    {
      "Id": 14920,
      "ParentId": 5819,
      "Code": "ODS",
      "Type": "Airport",
      "Name": "Одесса"
    },
    ...
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
    },
    ...
  ]
}
```
* Поле **Itineraries.DeeplinkUrl** перенаправляет на внешний сайт.
* Для следующенго запроса на потребуються поля: SessionKey, Itineraries.OutboundLegId и Itineraries.InboundLegId


##Получение данных деталей сессии (запрос типа GET)

Синтаксис
```
http://partners.api.skyscanner.net/apiservices/pricing/uk1/v1.0/
    {SessionKey}/booking/
    {OutboundLegId};
    {InboundLegId}?
    apiKey={apiKey}
```
Пример
```
http://partners.api.skyscanner.net/apiservices/pricing/uk1/v1.0/
    c5bf9d96668a45eb805afa927067c50f_rrsqbjcb_06a13f0a788e803fcc56e78802891a26/booking/
    14920-1705010740--32042-0-12428-1705010900;
    12428-1705072040--32042-0-14920-1705072200?
    apikey=prtl6749387986743898559646983194
```
Результат
```json
{
  "Segments": [
    {
      "Id": 1,
      "OriginStation": 14920,
      "DestinationStation": 12428,
      "DepartureDateTime": "2017-05-01T07:40:00",
      "ArrivalDateTime": "2017-05-01T09:00:00",
      "Carrier": 1401,
      "OperatingCarrier": 1401,
      "Duration": 80,
      "FlightNumber": "253",
      "JourneyMode": "Flight",
      "Directionality": "Outbound"
    },
    {
      "Id": 2,
      "OriginStation": 12428,
      "DestinationStation": 14920,
      "DepartureDateTime": "2017-05-07T20:40:00",
      "ArrivalDateTime": "2017-05-07T22:00:00",
      "Carrier": 1401,
      "OperatingCarrier": 1401,
      "Duration": 80,
      "FlightNumber": "258",
      "JourneyMode": "Flight",
      "Directionality": "Inbound"
    }
  ],
  "BookingOptions": [
    {
      "BookingItems": [
        {
          "AgentID": 3513089,
          "Status": "Pending",
          "Price": 2231.29,
          "Deeplink": "http://partners.api.skyscanner.net/apiservices/deeplink/v2?_cje=jzj5DawL5zJyT%2bnfeP9GJWfImnVvZd7vh0AJSObmdOp8YP07VbGmhzc%2bVTc80nUp&url=http%3a%2f%2fwww.apideeplink.com%2ftransport_deeplink%2f4.0%2fUA%2fru-ru%2fUAH%2fotua%2f2%2f14920.12428.2017-05-01%2c12428.14920.2017-05-07%2fair%2ftrava%2fflights%3fitinerary%3dflight%7c-32042%7c253%7c14920%7c2017-05-01T07%3a40%7c12428%7c2017-05-01T09%3a00%2cflight%7c-32042%7c258%7c12428%7c2017-05-07T20%3a40%7c14920%7c2017-05-07T22%3a00%26carriers%3d-32042%26passengers%3d1%26channel%3ddataapi%26cabin_class%3deconomy%26facilitated%3dfalse%26ticket_price%3d2231.29%26is_npt%3dfalse%26is_multipart%3dfalse%26client_id%3dskyscanner_b2b%26request_id%3d20cd20e1-4eab-481a-9f82-68fd7960662d%26deeplink_ids%3deu-central-1.prod_9bd5f84f0d8bb9538d278adf68f3c211%26commercial_filters%3dfalse%26q_datetime_utc%3d2017-03-03T08%3a26%3a22",
          "SegmentIds": [
            1,
            2
          ]
        }
      ]
    },
    ...
  ],
  "Places": [
    {
      "Id": 14920,
      "ParentId": 5819,
      "Code": "ODS",
      "Type": "Airport",
      "Name": "Одесса"
    },
    ...
  ],
  "Carriers": [
    {
      "Id": 1401,
      "Code": "M9",
      "Name": "Motor Sich Airlines",
      "ImageUrl": "http://s1.apideeplink.com/images/airlines/M9.png"
    }
  ],
  "Query": {
    "Country": "UA",
    "Currency": "UAH",
    "Locale": "ru-ru",
    "Adults": 1,
    "Children": 0,
    "Infants": 0,
    "OriginPlace": "5819",
    "DestinationPlace": "4110",
    "OutboundDate": "2017-05-01",
    "InboundDate": "2017-05-07",
    "LocationSchema": "Default",
    "CabinClass": "Economy",
    "GroupPricing": false
  }
}
```
