```Plain Text
@startuml

actor Пользователь as u
participant Сайт as s
queue "Очередь запросов" as db_qu
database БД as db

u -> s : Открыть поиск
activate s
s -> u : Вернуть страницу поиска

opt Поиск по фильтрам
u -> u : Добавить данные в поиск
end

u -> s : Найти задачи
s -> db_qu : Отправить запрос в БД
deactivate s

db <- db_qu : Получить запрос
activate db
db -> db : Выполнить запрос
db -> s : Вернуть ответ
deactivate db

activate s

alt Проверка ответа
s -> s : Отобразить задачи
u -> s : Посмотреть задачи
else Пустой ответ
s -> u !! : Предупреждение об отсутствии задач
end

deactivate s

@enduml
```