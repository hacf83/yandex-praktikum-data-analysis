# A/B-тестирование внедрения улучшенной рекомендательной системы

Статус проекта: завершен

## Описание проекта

Было проведено тестирование изменений, связанных с внедрением улучшенной рекомендательной системы. Ожидается, что за 14 дней с момента регистрации пользователи покажут улучшение каждой метрики не менее, чем на 10%:

* конверсия в просмотр карточки товара

* конверсия в просмотр корзины

* конверсия в покупку

Задачи:

* оценить корректность проведения теста

* проанализировать результаты теста

## Общий вывод

В проведении теста были обнаружены следующие ошибки:
    
* отсутствуют логи с 2020-12-31 по 2021-01-04

* новых пользователей из региона EU чуть меньше, чем планировалось (13,7% вместо 15%)

* аудитория не польностью состоит из пользователей региона EU

* в 1,6 раза меньше пользователей, чем ожидалось

* распределение сплитов по дням разное

* каждый четвертый пользователь принял участие в конкурирующем тесте

* каждый третий пользователь совершил хотя бы одно действие во время маркетинговой активности Christmas&New Year Promo

* есть пропуски промежуточных событий

* по каждой дате регистрации есть пользователи без событий. 14 декабря число пользователей без событий резко снизилось в группе A, скорее всего баг поправили только у группы A

<br>

Принятые меры по корректировке ошибок:

* удаление пользователей из регионов кроме EU

* удаление пользователей, принявших участие в конкрирующем тесте

* восстановление пропусков промежуточных событий

* удаление событий, которые произошли позднее 14 дня с момента регистрации

Пользователей, попавших под воздействие маркетинговой кампании, было решено не удалять, так как размер выборки тогда сократился бы очень сильно и у нас уже меньше пользователей, чем требовалось по ТЗ.

<br>

Пришлось удалить много наблюдений, часть ошибок не было возможным исправить. Как итог, к результатам теста мало доверия. Рекомендуется исправить все ошибки и перезапустить тест.

<br>

Метрики показали статистически значимое ухудщение:

|metric|lift|
|---|---|
|product_page_conversion|-0.10409|
|product_cart_conversion|-0.129553|
|purchase_conversion|-0.171234|