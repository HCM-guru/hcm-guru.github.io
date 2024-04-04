---
layout: default
title: API
nav_order: 3
---
# API

В процессе написания
{: .label .label-yellow }

[Реализация API](https://github.com/HCM-guru/webtutor-api) для WebSoft HCM.

## Зачем?

Данное API реализовано для сокращения времени разработки серверной части API на WebSoft HCM.

API уже включает в себя реализации для авторизации и валидации параметров запроса, что позволяют ускорить разработку новых компонентов.


### Структура

Благодаря четкой структуре файловой системы вам будет удобно реализовывать компоненты вашей системы.

```
src
└─── controllers
│   │   collaborators.ts
│   │   events.ts
|   |   my_custom_controller.js
|   | ...
└─── services
│   │   events.ts
│   │   file.ts
|   |   my_custom_service.js
|   | ...
└─── utils
    │   array.ts
    │   assert.ts
    |   my_custom_util.js
    | ...
```

## Как работает API?

API подразумевает под собой полный цикл REST API с авторизацей, валидацией параметров, формированием ответа сервера клиенту.

### Диаграмма состояния

```mermaid
stateDiagram-v2
  RequestProcessingStartState: Начало обработки запроса

  SearchingHandlerState: Поиск запрашиваемого обработчика в API
  HandlerNotFoundResponse: Обработчик не найден
  state IfHandlerFound <<choice>>

  ValidatingAuthorizationState: Авторизация пользователя/приложения
  UnauthorizedResponse: Ошибка авторизации
  state IfUnauthorized <<choice>>

  ValidatingPayloadState: Валидация параметров запроса
  UnprocessableEntityResponse: Некорректные параметры запроса
  state IfPayloadCorrect <<choice>>

  CallHandlerMethodState: Вызов метода с параметрами
  CreateAnswerObjectState: Формирование ответа сервера

  [*] --> RequestProcessingStartState

  RequestProcessingStartState --> SearchingHandlerState

  SearchingHandlerState --> IfHandlerFound
  IfHandlerFound --> HandlerNotFoundResponse
  HandlerNotFoundResponse --> CreateAnswerObjectState
  IfHandlerFound --> ValidatingAuthorizationState

  ValidatingAuthorizationState --> IfUnauthorized
  IfUnauthorized --> UnauthorizedResponse
  UnauthorizedResponse --> CreateAnswerObjectState
  IfUnauthorized --> ValidatingPayloadState

  ValidatingPayloadState --> IfPayloadCorrect
  IfPayloadCorrect --> UnprocessableEntityResponse
  UnprocessableEntityResponse --> CreateAnswerObjectState
  IfPayloadCorrect --> CallHandlerMethodState

  CallHandlerMethodState --> CreateAnswerObjectState

  CreateAnswerObjectState --> [*]
```