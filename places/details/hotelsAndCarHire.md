#Аренда авто и номеров отелей

##Places

* place_id - порядковый номер
* city_name - название города (может отсутствовать)
* admin_level1 - административная единица (может отсутствовать)
* country_name - название страны


##Results

* display_name - отображаемое имя
* parent_place_id - родительский идентификатор места
* individual_id - индивидуальный ключь места
* geo_type - тип места
* localised_geo_type - локализированый тип места
* is_bookable - логическое поле показывает пренадлежность к ресурсу booking.com


```json
{
  "places": [
    {
      "place_id": 2,
      "city_name": "Zaporizhia",
      "admin_level1": "Запорожская область",
      "country_name": "Украина"
    },
    ...
  ],
  "results": [
    {
      "display_name": "Zaporizhia (OZH)",
      "parent_place_id": 2,
      "individual_id": "114117160",
      "geo_type": "Airport",
      "localised_geo_type": "Аэропорт",
      "is_bookable": false
    },
    ...
  ]
}
```
