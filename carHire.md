#Ареда авто

[Глвня](https://github.com/tolyaganzin/skyscanner-RU) [<-Места](https://github.com/tolyaganzin/skyscanner-RU/blob/master/places.md) 

**Есть ряд замечаний к этому запросу**

* Может отработать не спервого раза (я делал по 2 запроса, если на второй не выдало ничего, тогда ареда отсутствует в базе, но это не совсем так) - кароче говоря кривота апихи
* Может отваливаться сервис (отдать ответ о длительном ожидании)
* На один и тот же запрос может отдать разное количество вариантов аренды авто
* {pickupplace}/{dropoffplace} данные поля могут содержать как **PlaceId** так и **долгота,широта**
* Возраст водителя должен бить от 21 до 75


###Запрос типа GET
Синтаксис
```
//Запрос
http://partners.api.skyscanner.net/apiservices/carhire/liveprices/v2/
    {market}/{currency}/{locale}/
    {pickupplace}/{dropoffplace}/
    {pickupdatetime}/{dropoffdatetime}/
    {driverage}?
    apiKey={apiKey}&
    userip={userip}}
//Заголовки
    Content-Type: application/x-www-form-urlencoded
    Accept: application/json
```

Пример
```
http://partners.api.skyscanner.net/apiservices/carhire/liveprices/v2/
    UA/UAH/ru-RU/
    ODS/ODS/
    2017-05-01T09:00/2017-05-02T18:00/
    21?
    apiKey=prtl6749387986743898559646983194&
    userip=127.0.0.1
```
###Уточнения
* Если масив авто пуст, значит нет доступных или их вовсе нет
* Количество вебсайтов может быть разное
* Количество картинок и класов авто - статично
* Количество класов авто - статично
* Поле cars.deeplink_url переадресовывает на внешний сайт выбранного авто

Результат
```json
{
  "submitted_query": {
    "market": "UA",
    "currency": "UAH",
    "locale": "ru-RU",
    "pickup_place": "ODS",
    "dropoff_place": "ODS",
    "pickup_date_time": "2017-05-01T09:00",
    "drop_off_date_time": "2017-05-02T18:00",
    "driver_age": "21"
  },
  "cars": [
    {
     "sipp": "CDMR",
     "image_id": 277847,
     "price_all_days": 3450.91,
     "seats": 5,
     "doors": 5,
     "bags": 3,
     "manual": true,
     "air_conditioning": true,
     "mandatory_chauffeur": false,
     "website_id": "argu",
     "vehicle": "Ford Focus или аналогичный",
     "deeplink_url": "http://partners.api.skyscanner.net/apiservices/deeplink/v2?_cje=jzj5DawL5zJyT%2bnfeP9GJWfImnVvZd7vh0AJSObmdOp8YP07VbGmhzc%2bVTc80nUp&url=http%3a%2f%2fwww.apideeplink.com%2fcarhire_deeplink%2f2.0%2fargu%2fcarhi%2fcar%2fUA%2cru%2cUAH%2fODS%2fODS%2f2017-05-01T09%3a00%3a00%2f2017-05-02T18%3a00%3a00%2f21%2fcars%2feu-west-1.prod_46b3ae8e529ce0bc7137f4872b804122%3fchannel%3ddataapi%26sipp%3dCDMR%26vendor%3dNational%26pickuproutenodeid%3d14920%26dropoffroutenodeid%3d14920&serviceType=CarHireDeeplink",
     "car_class_id": 3,
     "location": {
       "pick_up": {
         "address": "International Airport Odessa, Central airport St. 25, 65036",
         "distance_to_search_location_in_km": 0.8140665808,
         "geo_info": [
           46.427,
           30.678
         ]
       }
     },
     "value_add": {
       "fuel": {
         "type": "petrol",
         "policy": "full_to_full",
         "fair": true
       },
       "insurance": {
         "theft_protection": true,
         "third_party_cover": true,
         "free_collision_waiver": true
       },
       "young_driver_surcharge": true,
       "free_cancellation": true,
       "free_breakdown_assistance": true,
       "additional_drivers": {
         "paid": {
           "currency_id": "UAH",
           "price": 688.12
         }
       },
       "included_mileage": {
         "unlimited": true
       }
     }
   },
  ],
  "websites": [
    {
      "id": "sixt",
      "name": "Sixt",
      "image_url": "http://logos.skyscnr.com/images/websites/sixt.png",
      "in_progress": false,
      "optimised_for_mobile": true
    },
    {
      "id": "trjv",
      "name": "rentalcars.com",
      "image_url": "http://logos.skyscnr.com/images/websites/trjv.png",
      "in_progress": false,
      "optimised_for_mobile": true
    },
    {
      "id": "argu",
      "name": "Argus Car Hire",
      "image_url": "http://logos.skyscnr.com/images/websites/argu.png",
      "in_progress": true,
      "optimised_for_mobile": true
    },
    {
      "id": "holi",
      "name": "Holiday Autos",
      "image_url": "http://logos.skyscnr.com/images/websites/holi.png",
      "in_progress": true,
      "optimised_for_mobile": true
    }
  ],
  "images": [
    {
      "id": 356029,
      "url": "http://logos.skyscnr.com/images/carhire/sippmaps/ford_c-max.jpg"
    },
    ...
  ],
  "car_classes": [
    {
      "id": 1,
      "sort_order": 0,
      "name": "Мини"
    },
    {
      "id": 2,
      "sort_order": 1,
      "name": "Эконом класс"
    },
    {
      "id": 3,
      "sort_order": 2,
      "name": "Компакт"
    },
    {
      "id": 4,
      "sort_order": 3,
      "name": "Среднегабарит./стандарт"
    },
    {
      "id": 5,
      "sort_order": 4,
      "name": "Представительский"
    },
    {
      "id": 6,
      "sort_order": 5,
      "name": "Премиум/люкс"
    }
  ],
  "debug_items": [
    {
      "type": "Info",
      "title": "TimingProfiler Step",
      "content": "Step=CarHirePricingServiceClient::Poll, ElapsedMilliseconds=352"
    }
  ]
}
```
