#Request base .../{market or country}/{currency}/{locale}...

Практически во всех запросах skyscanner использует данную конструкцию. Она нужна для того, что бы полученый ответ приходил в указанной валюте и языке.

##Примеры
Начну я с конца данной части запроса так как для получения страны уже нужна локаль
###Получение {locale}
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

###Получение {currency}
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

###Получение {market or country}
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
