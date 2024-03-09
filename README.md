# ProfItmo
## Описание методов

## Заказчик

### Регистрация - POST api/v1/customers/register
```
request: {"name": "Иван", "phone": "1234567890", "email": "ivan@gmail.com", "password": "********"}
response: {"customerID": "4w5l6jn4wlk5j6nw4lk56"}
```

### Авторизация - POST api/v1/customers/login
```
request: {"email": "ivan@example.com", "password": "********"}
response: {"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."}
```

### Изменить аккаунт - PUT api/v1/customers/{customerID}
```
request: {"name": "Новое имя", "phone": "новый_номер", "email": "новый_email", "password": "новый_пароль"}
response: {"message": "Аккаунт успешно изменен"}
```

### Удалить аккаунт - DELETE api/v1/customers/{customerID}
```
response: {"message": "Аккаунт успешно удален"}
```

### Заказывать услугу - POST api/v1/customers/{customerID}/orders
```
request: {"serviceID": "уникальный_идентификатор_услуги", “servis_name”: “название_услуги”, “description”: “описание_услуги”, “date_start”: “дата_начала”, “date_finish”: “дата_завершения”, "price": “стоимость”, "customerID": {customerID}, "executorID": {executorID}, “comment”: “комментарий”,  “status”: “статус”}
response: {"orderID": "уникальный_идентификатор_заказа"}
```

### Создать объявление - POST api/v1/customers/{customerID}/advertisements
```
request: {"advertisement_name": "название_объявления", "description": "описание_объявления",  “date_start”: “дата_начала”, “date_finish”: “дата_завершения”, "price": “стоимость”, "customerID": {customerID}, “comment”: “комментарий”}
response: {"advertisementID": "уникальный_идентификатор_объявления"}
```

### Изменить объявление - PUT api/v1/customers/{customerID}/advertisements/{advertisementID}
```
request: {"advertisement_name": "новое_название_объявления", "description": "новое_описание_объявления",  “date_start”: “новоя_дата_начала”, “date_finish”: “новоя_дата_завершения”, "price": “новоя_стоимость”, "customerID": {customerID}, "executorID": {executorID}, “comment”: “новый_комментарий”,  “status”: “новый_статус”}
response: {"message": "Объявление успешно изменено"}
```

### Удалить объявление - DELETE api/v1/customers/{customerID}/advertisements/{advertisementID}
```
response: {"message": "Объявление успешно удалено"}
```

### Оплатить услугу - POST api/v1/payments
```
request: {"serviceID": "уникальный_идентификатор_услуги", "amount":“стоимость”}
response: {"paymentId": "уникальный_идентификатор_платежа"}
```

### Получить информацию о платеже - GET api/v1/payments/{paymentId}
```
response: {"paymentId": "уникальный_идентификатор_платежа", "customerId": "уникальный_идентификатор_заказчика", "paymentDate": "2024-03-05", "amount": 100.0, "status": "Оплачен"}
```

## Исполнитель

### Регистрация Исполнителя - POST api/v1/executors/register
```
request: {"name": "Иван", "phone": "1234567890", "email": "ivan@gmail.com", "password": "********", "experience": "5 years", "serviceArea": "IT"}
response: {"executorID": "4w5l6jn4wlk5j6nw4lk56"}
```

### Авторизация Исполнителя - POST api/v1/executors/login
```
request: {"email": "ivan@example.com", "password": "********"}
response: {"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."}
```

### Изменить аккаунт Исполнителя - PUT api/v1/executors/{executorID}
```
request: {"name": "Новое имя", "phone": "новый_номер", "email": "новый_email", "password": "новый_пароль", "experience": "10 years", "serviceArea": "Lawyer"}
response: {"message": "Аккаунт успешно изменен"}
```

### Удалить аккаунт Исполнителя - DELETE api/v1/executors/{executorID}
```
response: {"message": "Аккаунт успешно удален"}
```

### Откликнуться на объявление - POST api/v1/executors/{executorID}/responses
```
request: {"advertisementID": "уникальный_идентификатор_объявления"}
response: {"orderID": "уникальный_идентификатор_заказа"}
```


## Описание сущностей

## Заказчик

__Атрибуты:__

* ID __PK__
* Имя
* Номер телефона
* Email
* Пароль


__Методы:__
* Регистрация
* Авторизация
* Изменить аккаунт
* Удалить аккаунт
* Заказывать услугу
* Создать объявление
* Изменить объявление
* Удалить объявление
* Оплата



## Исполнитель

__Атрибуты:__
* ID __PK__
* Имя
* Номер телефона
* Email
* Опыт работы
* Сфера услуг
* Пароль

__Методы:__
* Регистрация
* Авторизация
* Изменить аккаунт
* Удалить аккаунт
* Откликнуться на объявление


## Объявление
__Атрибуты:__
* ID Объявления __PK__
* Название
* Описание
* Дата начала
* Дата конца
* Стоимость
* ID Заказчика __FK__
* ID Исполнителя __FK__
* ID Платежа __FK__
* Комментарии


## Платеж
__Атрибуты:__
* ID платежа __PK__
* ID заказчика __FK__
* Дата оплаты
* Стоимость
* Статус (Оплачен/Не оплачен)


## Заказ
__Атрибуты:__
* ID заказа __PK__
* ID исполнителя __FK__
* ID заказчика __FK__
* Дата заказа __FK__
* Описание __FK__
* Статус (Не Выполнен, В работе, Выполнен, Отменен)
* Статус оплаты (Оплачен, не оплачен)FK