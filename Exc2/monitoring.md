### Мотивация

Бизнес не хочет терять заказы из-за потенциальных сбоев работоспособности системы, наступление которых можно будет заметить заранее
и вовремя принять меры, если будет корректно настроен мониторинг. Компания активно развивается,
и без мониторинга невозможно будет найти узкие места в системе, которые скажутся при росте количества пользователей на работе системы

Необходимо даже при стабильной работе системы следить за ее состоянием

Плюс можно будет получить какую то неожиданную информацию о работе системы

### Выбор подхода к мониторингу

4 золотых сигнала хорошо подходит, т.к. хотим следить
- за изменением во времени количества запросов на каждый бэкенд-сервис
(у нас есть внутренние + внешние пользователи, которые ходят в систему по предоставляемому апи)
- за временем ответа сервисов
- плюс за загрузкой CPU и RAM, т.к есть CPU bound задачи

### Отслеживаемые метрики
На первом этапе выбираем следующие метрики

Нужно следить за брокером, не скапливаются ли сообщения
- Number of dead-letter-exchange letters in RabbitMQ
- Number of message in flight in RabbitMQ
- Number of messages in queues in RabbitMQ

Следим за RPS везде, чтобы понимать текущую нагрузку на сервис, понимать где и когда бывают пики нагрузки,
оценивать максимально возможный RPS
- Number of requests (RPS) for internet shop API
- Number of requests (RPS) for CRM API
- Number of requests (RPS) for MES API

Следим за загрузкой ЦП
- CPU % for shop API
- CPU % for CRM API
- CPU % for MES API

Нет ли утечек памяти?
- Memory Utilisation for shop API
- Memory Utilisation for CRM API
- Memory Utilisation for MES API

Важная метрика - время ответа, если растет - это может говорить о том, что сервис перестает справляться с нагрузкой
- Response time (latency) for shop API
- Response time (latency) for CRM API
- Response time (latency) for MES API

Размер S3 хранилища должен быть заранее посчитан с запасом, но хорошо бы узнать, когда он начнет забиваться объектами
- Size of S3 storage

Следим за числом критических ошибок, в идеале не должно их быть
- Number of HTTP 500 for shop API
- Number of HTTP 500 for CRM API
- Number of HTTP 500 for MES API

Более детальные метрики планируется добавлять по мере необходимости


### План действий
