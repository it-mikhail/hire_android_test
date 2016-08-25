Тестовое задание на позицию Android-разработчика
==================

- Все неоднозначности описания данного задания трактуются в пользу кандидата. При этом всегда можно уточнить отдельные моменты.
- Допустимо уменьшать бизнес-требования этого задания, сокращая или модифицируя его в случае, если та или иная функция несоразмерно увеличивает трудоемкость работ или видится нецелесообразной по тем или иным причинам. При предоставлении результата добавить пояснение, о том, какая часть убрана из задания и по каким причинам.
- Исходные данные допустимо преобразовывать в иную форму представления, сохраняя при этом сам состав информации и предоставив само преобразование в виде утилиты или иного способа.
- Оцениваться будет как функционал, так и код, включая крайние и не основные случаи поведения и оформление кода, включая его структурирование и комментирование.
- Ограничений на используемые компоненты и библиотеки нет.

Хотелось бы увидеть содержательные комментарии в коде там, где это необходимо. 

Расскажите нам, как вы тестировали результат своей работы, какие используете инструменты и как вы осуществляете тестирование. Наличие юнит-тестов и авто-тестов в проекте будет существенным плюсом.
 
Результат выполнения задания нужно оформить здесь же, на гитхабе. В качестве ответа просто пришлите ссылку на свой репозиторий. Мы используем `Git`, и если вы его не знаете, вам стоит освоить базу самостоятельно.

### Что необходимо сделать

Приложение, имеющее вертикальное меню с двумя разделами: "Расписание" и "О приложении"

#### 1. "Расписание"

Первый экран раздел должен позволять выбрать:

 - Станцию «отправления»
 - Станцию «прибытия».
 - Дату отправления.

Экран выбора станции должен:  

- Содержать общий перечень станций (см. вложенный файл), сгруппированный по значению «Страна, Город». Полный перечень групп и элементов должен быть представлен на одном экране, с возможностью пролистывания всего содержимого.
- Предоставлять возможность поиска по части имени (как начальной, так и входящей, независимо от регистра). Поиск необходимо осуществлять на том же экране, где представлен список станций.
- Предоставлять возможность просмотра детальной информации о конкретной станции (именование и ее полный адрес, включая город, регион и страну).

#### 2. "О приложении"

В данном разделе необходимо разместить информацию о:

 - Копирайте
 - Версии приложения

### Описание файла с данными
Предполагается, что данные станций изменяются примерно раз в 3 месяца и изменения незначительны.

Входные данные предоставлены в формате JSON
```javascript
{
  "citiesFrom" : [  ], //массив пунктов отправления
  "citiesTo" : [  ] //массив пунктов назначения
}
```
Элемент массива представляет собой описание города
```javascript
{
	"countryTitle" : "Россия", //название страны
	"point" : { //координаты города
		"longitude" : 50.64357376098633,
		"latitude" : 55.37233352661133
	},
	"districtTitle" : "Чистопольский район", //название района
	"cityId" : 4454, //идентификатор города
	"cityTitle" : "Чистополь", //название города
	"regionTitle" : "Республика Татарстан", //название региона
	"stations" : [...] //массив станций
}
```

Станция описывается объектом
```javascript
{
	"countryTitle" : "Россия", //название страны (денормализация данных, дубль из города)
	"point" : { //координаты станции (в общем случае отличаются от координат города)
		"longitude" : 50.64357376098633,
	    "latitude" : 55.37233352661133
	},
	
	"districtTitle" : "Чистопольский район", //название района
	"cityId" : 4454, //идентификатор города
	"cityTitle" : "город Чистополь", //название города
	"regionTitle" : "Республика Татарстан", //название региона
	
	"stationId" : 9362, //идентификатор станции
	"stationTitle" : "Чистополь" //полное название станции
}
```
### Удачи!
