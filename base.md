#Request base .../{market or country}/{currency}/{locale}...

Практически во всех запросах **skyscanner** использует данную конструкцию. Она нужна для того, что бы полученый ответ приходил в указанной валюте и языке.

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
Результат

```json
{
  "Locales": [
    {
      "Code": "ar-AE",
      "Name": "العربية (الإمارات العربية المتحدة)"
    },
    {
      "Code": "az-AZ",
      "Name": "Azərbaycan\u00adılı (Azərbaycan)"
    },
    {
      "Code": "bg-BG",
      "Name": "български (България)"
    },
    {
      "Code": "ca-ES",
      "Name": "català (català)"
    },
    {
      "Code": "cs-CZ",
      "Name": "čeština (Česká republika)"
    },
    {
      "Code": "da-DK",
      "Name": "dansk (Danmark)"
    },
    {
      "Code": "de-DE",
      "Name": "Deutsch (Deutschland)"
    },
    {
      "Code": "el-GR",
      "Name": "Ελληνικά (Ελλάδα)"
    },
    {
      "Code": "en-GB",
      "Name": "English (United Kingdom)"
    },
    {
      "Code": "en-GG",
      "Name": "English (United Kingdom)"
    },
    {
      "Code": "en-US",
      "Name": "English (United States)"
    },
    {
      "Code": "es-ES",
      "Name": "Español (España)"
    },
    {
      "Code": "es-MX",
      "Name": "Español (México)"
    },
    {
      "Code": "et-EE",
      "Name": "eesti (Eesti)"
    },
    {
      "Code": "fi-FI",
      "Name": "suomi (Suomi)"
    },
    {
      "Code": "fr-FR",
      "Name": "français (France)"
    },
    {
      "Code": "hr-HR",
      "Name": "hrvatski (Hrvatska)"
    },
    {
      "Code": "hu-HU",
      "Name": "magyar (Magyarország)"
    },
    {
      "Code": "id-ID",
      "Name": "Bahasa Indonesia (Indonesia)"
    },
    {
      "Code": "it-IT",
      "Name": "italiano (Italia)"
    },
    {
      "Code": "ja-JP",
      "Name": "日本語 (日本)"
    },
    {
      "Code": "ko-KR",
      "Name": "한국어 (대한민국)"
    },
    {
      "Code": "lt-LT",
      "Name": "lietuvių (Lietuva)"
    },
    {
      "Code": "lv-LV",
      "Name": "latviešu (Latvija)"
    },
    {
      "Code": "ms-MY",
      "Name": "Bahasa Melayu (Malaysia)"
    },
    {
      "Code": "nb-NO",
      "Name": "norsk, bokmål (Norge)"
    },
    {
      "Code": "nl-NL",
      "Name": "Nederlands (Nederland)"
    },
    {
      "Code": "pl-PL",
      "Name": "polski (Polska)"
    },
    {
      "Code": "pt-BR",
      "Name": "Português (Brasil)"
    },
    {
      "Code": "pt-PT",
      "Name": "português (Portugal)"
    },
    {
      "Code": "ro-RO",
      "Name": "română (România)"
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
    {
      "Code": "th-TH",
      "Name": "ไทย (ไทย)"
    },
    {
      "Code": "tl-PH",
      "Name": "Filipino (Pilipinas)"
    },
    {
      "Code": "tr-TR",
      "Name": "Türkçe (Türkiye)"
    },
    {
      "Code": "uk-UA",
      "Name": "українська (Україна)"
    },
    {
      "Code": "vi-VN",
      "Name": "Tiếng Việt (Việt Nam)"
    },
    {
      "Code": "zh-CN",
      "Name": "简体中文"
    },
    {
      "Code": "zh-HK",
      "Name": "中文(香港特別行政區)"
    },
    {
      "Code": "zh-SG",
      "Name": "中文(新加坡)"
    },
    {
      "Code": "zh-TW",
      "Name": "繁體中文"
    }
  ]
}
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
