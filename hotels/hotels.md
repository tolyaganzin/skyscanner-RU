
#Отели

[Глвня](https://github.com/tolyaganzin/skyscanner-RU) [<-Места](https://github.com/tolyaganzin/skyscanner-RU/blob/master/places/places.md) | [Аренда авто->](https://github.com/tolyaganzin/skyscanner-RU/blob/master/carHire/carHire.md)

* Places [офф документация](https://skyscanner.github.io/slate/#places)
* Hotels Price List and Hotels Details service [офф документация](https://support.business.skyscanner.net/hc/en-us/articles/212098705-Hotels-Price-List-and-Hotels-Details-service#createdetails)

------------------------------------------------------------------------------------------

* Получение всех мест из запроса [перейти](https://github.com/tolyaganzin/skyscanner-RU/blob/master/places/places.md#Аренда-авто-и-номеров-отелей-запрос-типа-get)
* Получение уникального идинтификатора места (отеля) [перейти](#Получение-отелей-и-цен-по-идентификатору-individual_id-из-результата-запроса-выше-запрос-типа-get)
* Подробная информация об отеле [перейти](#Получение-подробной-информации-об-отеле-запрос-типа-get)


##Получение отелей и цен по идентификатору individual_id из результата запроса выше (запрос типа GET)
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
Результат
```json
{
  "hotels_prices": [
    {
      "id": 95823343,
      "agent_prices": [
        {
          "id": 46,
          "price_total": 151
        }
      ]
    },
    ...
  ],
  "hotels": [
    {
      "name": "Venecia Hotel & Spa",
      "types": [
        "Отель"
      ],
      "hotel_id": 95823343,
      "address": ", ",
      "district": 0,
      "number_of_rooms": 0,
      "amenities": [
        1,
        ...
      ],
      "latitude": 47.83651,
      "longitude": 35.10544,
      "image_urls": [
        "d3ba47lalua02r.cloudfront.net/available{/64861407/:{rmt.jpg:[200,200],rmc.jpg:[628,470],morig.jpg:[1000,747],mc.jpg:[314,235],rmf.jpg:[1000,747],provider:177,rmca.jpg:[627,470],order:0}}"
      ],
      "images": {
        "/64861407/": {
          "rmt.jpg": [
            200,
            200
          ],
          ...
        }
      },
      "score": 0,
      "tag": "AVAILABLE",
      "star_rating": 3,
      "distance_from_search": 1.861
    },
    ...
  ],
  "agents": [
    {
      "id": 17,
      "name": "Hotels.com",
      "image_url": "http://s1.apideeplink.com/images/websites/220x80/h_hc.png",
      "in_progress": false
    },
    ...
  ],
  "amenities": [
    {
      "id": 44,
      "name": "Банкомат",
      "key": "CASHMACHINE"
    },
    ...
  ],
  "places": [],
  "urls": {
    "hotel_details": "/apiservices/hotels/livedetails/v2/details/H4sIAAAAAAAEAKtWyleyilYKdVTSUSoq1Q0KBdKhwS5A0tDQxMTE0tTEEsg2MjA01zUw1TUwCTEwsAIjJFFDAyRRIx1DoF5jHSMgw9RQSSevNCcnVkcpT8lK18jM0ti0FgB8awdccgAAAA2?apikey=_eTuWCL8cvqh2T-KnL9chOQHAyuJCOS4V-W8IYYSyfIB-BMOol_84rUU5YwpUs91fMuqY2e3PFUj88i_NwREGug%3D%3D"
  },
  "status": "COMPLETE",
  "total_hotels": 39,
  "total_available_hotels": 5,
  "last_update": 1489056627386,
  "image_host_url": "d3ba47lalua02r.cloudfront.net/available",
  "debug_items": [
    {
      "type": "Info",
      "title": "TimingProfiler Step",
      "content": "Step=HotelsPricingServiceClient::Poll, ElapsedMilliseconds=22"
    }
  ]
}
```
* hotels_prices - содержит id отелей и и цены, а так же саму цену
* hotels - масив объектов отелей
* agents - агенции предлагающие данный отель
* amenities - масив доступных объектов услуг по всем отелям из запроса
* places - места
* urls - ссылка на детальное описание отлей
* отладочная информация

##Получение подробной информации об отеле (запрос типа GET)

Синтаксис
```
http://partners.api.skyscanner.net/apiservices/hotels/livedetails/v2/details/
    {session key}?
    apiKey={encryptedApiKey}
    &HotelIds={hotelIds}
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
    H4sIAAAAAAAEAKtWyleyilYKdVTSUSoq1Q0KBdKhwS5A0tDQxMTE0tTEEsg2MjA01zUw1TUwCTEwsAIjJFFDAyRRIx1DoF5jHSMgw9RQSSevNCcnVkcpT8lK18jM0ti0FgB8awdccgAAAA2?
    apikey=_eTuWCL8cvqh2T-KnL9chOQHAyuJCOS4V-W8IYYSyfIB-BMOol_84rUU5YwpUs91fMuqY2e3PFUj88i_NwREGug%3D%3D&
    HotelIds=95823343
```

###Уточнение
* {session key} и {encryptedApiKey} - действуют достаточно не долго (примерно 12 часов)
* Если в поле **hotelIds** нужно передать более одного параметра - их нужно разделить запятой.
* Но при ответе мы получим пустой масив **hotels_prices**, а остальные данные дополняться в соответствии с запросом. Это не страшно так как цены отелей были в запросе выше.
```
hotelIds=95823343,46999735,56665948
```

Результат
```json
{
  "hotels_prices": [
    {
      "id": 95823343,
      "agent_prices": [
        {
          "id": 46,
          "price_per_room_night": 26,
          "price_total": 151,
          "available_rooms": 5,
          "deeplink": "/hotel_deeplink/4.0/UA/ru-RU/USD/h_ov/95823343/2017-05-04/2017-05-10/hotel/hotel/hotels?rooms_left=1&deeplink_ids=eu-central-1.prod_b2599c21e4f7d7ad23705a88e1f8b05c&q_datetime_utc=2017-03-09T11%3A09%3A04&guests=2&request_id=fde80984-ad70-4238-9791-f618b51ea748&legacy_provider_id=46&ticket_price=151&rooms=1&max_price=151.0",
          "booking_deeplink": "http://partners.api.skyscanner.net/apiservices/deeplink/v2?_cje=jzj5DawL5zJyT%2bnfeP9GJWfImnVvZd7vh0AJSObmdOp8YP07VbGmhzc%2bVTc80nUp&url=www.skyscanner.com.ua%2fhotel_deeplink%2f4.0%2fUA%2fru-RU%2fUSD%2fh_ov%2f95823343%2f2017-05-04%2f2017-05-10%2fhotel%2fhotel%2fhotels%3frooms_left%3d1%26deeplink_ids%3deu-central-1.prod_b2599c21e4f7d7ad23705a88e1f8b05c%26q_datetime_utc%3d2017-03-09T11%253A09%253A04%26guests%3d2%26request_id%3dfde80984-ad70-4238-9791-f618b51ea748%26legacy_provider_id%3d46%26ticket_price%3d151%26rooms%3d1%26max_price%3d151.0&serviceType=HotelsDeeplink",
          "room_offers": [
            {
              "policy_dto": {
                "cancellation": "Бесплатная отмена",
                "cancellation_code": 1
              },
              "rooms": [
                {
                  "adults": 0,
                  "children": 0,
                  "type": "Двухместный номер",
                  "type_id": "ROOMTYPE_DOUBLE"
                }
              ],
              "available": 1
            },
          ...
          ]
        }
      ],
      "reviews_count": 0,
      "ratings": [
        {
          "name": "Room",
          "localised_name": "Номер",
          "score": 0,
          "examples": []
        },
        ...
      ],
      "guests": [
        {
          "ratio": 0,
          "description": "Индивидуальные путешественники"
        },
        ...
      ]
    }
  ],
  "hotels": [
    {
      "name": "Venecia Hotel & Spa",
      "hotel_id": 95823343,
      "address": "Nizhnedneprovskaya Street 1B; 69000 Запорожье",
      "district": 0,
      "number_of_rooms": 0,
      "amenities": [
        0,
        2,
        4,
        2,
        6,
        8,
        10
      ],
      "latitude": 47.83651,
      "longitude": 35.10544,
      "images": {
        "/64861706/": {
          "mf.jpg": [
            1000,
            500
          ],
          ...
        },
        ...
        "score": 0,
        "star_rating": 3
      },
    }
  ],
  "agents": [
    {
      "id": 46,
      "name": "Ostrovok",
      "image_url": "http://s1.apideeplink.com/images/websites/220x80/h_ov.png",
      "in_progress": false
    }
  ],
  "amenities": [
    {
      "id": 0,
      "name": "Парковка",
      "key": "PARKING",
      "parent": 1
    },
    {
      "id": 1,
      "name": "Парковка и транспорт",
      "image": "http://www.skyscanner.net/hotels/images/amenities/ParkingAndTransport.png",
      "key": "PARKINGANDTRANSPORT"
    },
    ...
  ],
  "places": [
    {
      "id": 0,
      "name": "Запорожье"
    },
    {
      "id": 1,
      "name": "Запорожская область"
    },
    {
      "id": 2,
      "name": "Украина"
    }
  ],
  "status": "COMPLETE",
  "total_hotels": 0,
  "total_available_hotels": 0,
  "last_update": 0,
  "image_host_url": "d3ba47lalua02r.cloudfront.net/available",
  "base_host_url": "www.skyscanner.com.ua",
  "debug_items": [
    {
      "type": "Info",
      "title": "TimingProfiler Step",
      "content": "Step=HotelsPricingServiceClient::GetHotelDetails, ElapsedMilliseconds=15"
    }
  ]
}
```
