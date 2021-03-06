## Проект часть I

### Data Analysis & ClickHouse

В первом задании по проекту вам нужно будет исследовать данные и ответить на несколько аналитических вопросов. 

Представьте, что вы устроились работать аналитиком в отдел рекламы, и ваша первая задача - помочь коллегам разобраться с некоторыми вопросами:

1. Получить статистику по дням. Просто посчитать число всех событий по дням, число показов, число кликов, число уникальных объявлений и уникальных кампаний.
2. Разобраться, почему случился такой скачок 2019-04-05? Каких событий стало больше? У всех объявлений или только у некоторых?
3. Найти топ 10 объявлений по CTR за все время. CTR — это отношение всех кликов объявлений к просмотрам. Например, если у объявления было 100 показов и 2 клика, CTR = 0.02. Различается ли средний и медианный CTR объявлений в наших данных?
4. Похоже, в наших логах есть баг, объявления приходят с кликами, но без показов! Сколько таких объявлений, есть ли какие-то закономерности? Эта проблема наблюдается на всех платформах?
5. Есть ли различия в CTR у объявлений с видео и без? А чему равняется 95 процентиль CTR по всем объявлениям за 2019-04-04?
6. Для финансового отчета нужно рассчитать наш заработок по дням. В какой день мы заработали больше всего? В какой меньше? Мы списываем с клиентов деньги, если произошел клик по CPC объявлению, и мы списываем деньги за каждый показ CPM объявления, если у CPM объявления цена - 200 рублей, то за один показ мы зарабатываем 200 / 1000.
7. Какая платформа самая популярная для размещения рекламных объявлений? Сколько процентов показов приходится на каждую из платформ (колонка platform)?
8. А есть ли такие объявления, по которым сначала произошел клик, а только потом показ?

* [Документация](https://clickhouse.yandex/docs/ru/) — очень важный навык)
* [Что такое CTR/CPM/CPC?](https://www.e-xecutive.ru/wiki/index.php/CPM,_CTR_%D0%B8_CPC-%D0%BF%D0%BE%D0%BA%D0%B0%D0%B7%D0%B0%D1%82%D0%B5%D0%BB%D0%B8_%D0%B2_%D0%B8%D0%BD%D1%82%D0%B5%D1%80%D0%BD%D0%B5%D1%82-%D1%80%D0%B5%D0%BA%D0%BB%D0%B0%D0%BC%D0%B5)

##### Структура таблицы `ads_data` следующая:

* `date` - день, в который происходят события
* `time` - точное время события
* `event` - тип события, может быть или показ или клик по рекламе
* `platform` - платформа, на которой произошло рекламное событие
* `ad_id` - id рекламного объявления
* `client_union_id` - id рекламного клиента
* `campaign_union_id` - id рекламной кампании
* `ad_cost_type` - тип объявления с оплатой за клики (CPC) или за показы (CPM)
* `ad_cost` - стоимость объявления в рублях, для CPC объявлений - это цена за клик, для CPM - цена за 1000 показов
* `has_video` - есть ли у рекламного объявления видео
* `target_audience_count` - размер аудитории, на которую таргетируется объявление

*В таблице 1 миллион значений! Это значит, что нужно следить за запросами, не забывать добавлять лимиты!*
 
##### Рецензия преподавателя:
```
Все супер
```
