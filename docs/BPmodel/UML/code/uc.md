```Plain Text
@startuml

actor Пользователь as u
actor Система as sys
actor "База данных" as db

package Поиск {
usecase "Открыть поиск" as ofUC
usecase "Добавить данные" as adUC
usecase "Нажать кнопку 'Найти'" as ftUC
usecase "Посмотреть задачи" as stUC
usecase "Получить предупреждение об отсутствии задач" as ap_rmUC

usecase "Отправить запрос в БД" as srUC
usecase "Получить ответ от БД" as raUC
usecase "Отобразить задачи" as dtUC
usecase "Выдать предупреждение об отсутствии задач" as ap_smUC

usecase "Получить запрос" as db_rrUC
usecase "Выполнить запрос" as db_erUC
usecase "Вернуть ответ" as db_raUC
}

u --> ofUC
u --> adUC
u --> stUC
u --> ap_rmUC

sys --> srUC
sys --> raUC
sys --> dtUC
sys --> ap_smUC

db --> db_rrUC
db --> db_erUC
db --> db_raUC


dtUC ..> raUC : include
srUC ..> ftUC : include
db_raUC ..> db_erUC : include
ftUC ..> ofUC : include
stUC ..> dtUC : include
db_rrUC ..> srUC : include
raUC ..> db_raUC : include
db_erUC ..> db_rrUC : include
ap_rmUC ..> ap_smUC : include

ftUC <.. adUC : extend

@enduml
```