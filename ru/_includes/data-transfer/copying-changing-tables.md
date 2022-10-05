Выбор того или иного типа трансфера зависит от характера изменений данных на эндпоинте-источнике. 

Например, если на реплицируемом источнике есть таблица, которая регулярно обновляется почти целиком, то за короткий промежуток времени в WAL накапливается большой объем данных, поскольку таблица за этот период перезаписывается несколько раз. Обработка изменений в таких случая потребует много времени и значительных ресурсов. Поэтому вместо репликации целесообразно настроить копирование с регулярной активацией и перезаписывать таблицу целиком в консистентном и свежем состоянии. См. [Создание трансфера](../../data-transfer/operations/transfer.md) для подробной информации о типах и настройках трансфера.