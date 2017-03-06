#Request base .../{market or country}/{currency}/{locale}...

[Глвня](https://github.com/tolyaganzin/skyscanner-RU) [Отели->](https://github.com/tolyaganzin/skyscanner-RU/blob/master/hotels.md)

###Localisation [офф документация](https://skyscanner.github.io/slate/#localisation)

-------------------------------------------------------------------------------------------------------------------

* Практически во всех запросах **skyscanner** использует данную конструкцию.
* Она нужна для того, что бы полученый ответ приходил в указанной валюте и языке.
* Страны нужны для получение более точной цены на билет самолета либо аренду авто или номера отеля.


##Примеры
Начну я с конца данной части запроса так как для получения страны уже нужна локаль.


###Получение {locale} (запрос типа GET)

Синтаксис
```
http://partners.api.skyscanner.net/apiservices/
    reference/v1.0/locales?
    apiKey={apiKey}
```

Пример
```
http://partners.api.skyscanner.net/apiservices/
    reference/v1.0/locales?
    apikey=prtl6749387986743898559646983194
```

Результат - **JSON** ответ с масивом объектов локалей. В адресной строке мы будем постоянно использовать поле **"Code"**.
```json
{
  "Locales": [
    {
      "Code": "uk-UA",
      "Name": "українська (Україна)"
    },   
    {
      "Code": "bg-BG",
      "Name": "български (България)"
    },
    {
      "Code": "en-US",
      "Name": "English (United States)"
    },
    {
      "Code": "pl-PL",
      "Name": "polski (Polska)"
    },
    {
      "Code": "ru-RU",
      "Name": "русский (Россия)"
    },
    {
      "Code": "sk-SK",
      "Name": "slovenčina (Slovenská republika)"
    },
    {
      "Code": "sv-SE",
      "Name": "svenska (Sverige)"
    },
    ...
  ]
}
```
* Name - название локали на ее локале
* **Code** - это и есть локаль работает как так "uk-UA" так и вот так "UA", но лучше всего первый вариант **.../uk-UA...**



###Получение {currency} (запрос типа GET)

Синтаксис
```
http://partners.api.skyscanner.net/apiservices/
    reference/v1.0/currencies?
    apiKey={apiKey}
```

Пример
```
http://partners.api.skyscanner.net/apiservices/
    reference/v1.0/currencies?
    apikey=prtl6749387986743898559646983194
```

Результат
```json
{
  "Currencies": [
      {
          "Code": "USD",
          "Symbol": "$",
          "ThousandsSeparator": ",",
          "DecimalSeparator": ".",
          "SymbolOnLeft": true,
          "SpaceBetweenAmountAndSymbol": false,
          "RoundingCoefficient": 0,
          "DecimalDigits": 2
      },
  ...
  ]
}
```
###Статические поля ответа
* ThousandsSeparator - разделитель каждой тысячи
* DecimalSeparator - целочисленный разделитель
* RoundingCoefficient - коэффициент округления

###Динамические поля
* **Code** - код валюты указываеться в запросе **.../USD...**
* Symbol - символ валюты
* SymbolOnLeft - расположение символа валюты
* SpaceBetweenAmountAndSymbol - наличие пробела между символом валюты и числом
* DecimalDigits - количество допустимых символов после **DecimalSeparator**


###Получение {market or country} (запрос типа GET)

Синтаксис
```
http://partners.api.skyscanner.net/apiservices/
    reference/v1.0/countries/
    {locale}?
    apiKey={apiKey}
```

Пример
```
http://partners.api.skyscanner.net/apiservices/
    reference/v1.0/countries/
    en-US?
    apikey=prtl6749387986743898559646983194
```

Результат
```json
{
  "Countries": [
    {
      "Code": "AD",
      "Name": "Andorra"
    },
    {
      "Code": "AE",
      "Name": "United Arab Emirates"
    },
    {
      "Code": "AF",
      "Name": "Afghanistan"
    },
  ...
  ]
}
```
* **Code** - код страны указываеться в запросе **.../AF...**
* Name - название страны на языке с указанной локалью в нашем запросе
