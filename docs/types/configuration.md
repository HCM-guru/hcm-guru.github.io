---
layout: default
title: Конфигурация
parent: Типы
nav_order: 1
---

## Конфигурация

Актуально
{: .label .label-green }

Типы доступны в проектах как для _typescript_, так и для проектов на _javascript_

### Установка

Для работы типов необходимо установить _typescript 4.4.4_

{: .note }
Почему именно [typescript 4.4.4?]({% link docs/faq/index.md %}#Почему-версия-4.4.4?)

```bash
npm i typescript@4.4.4
```

Далее необходимо установить зависимость с типами

```bash
npm i @umbrik/webtutor-types
# or
npm i @umbrik/webtutor-types@{необходимая_версия}
```

### Генерация конфигурации

После этого необходимо сгенерировать _tsconfig.json_

Генерируем конфиг, либо просто создаем вручную файл tsconfig.json

```bash
npx tsc -init
```

Далее добавляем в _tsconfig_ следующие строки:

```jsonc
{
  // Отключение автоматической загрузки любых типов/библиотек
  "noLib": true,
  // Типы для WebSoft HCM
  "typeRoots": [
    "node_modules/@umbrik/webtutor-types/lib",
    "node_modules/@umbrik/webtutor-types/lib/xml"
  ]
}
```

Пример _tsconfig.json_

```jsonc
{
  "compilerOptions": {
    "target": "es5",
    "module": "es6",
    "esModuleInterop": true,
    "strict": false,
    "noImplicitAny": true,
    "allowJs": true,
    "isolatedModules": true,
    "moduleResolution": "node",
    "baseUrl": "src",
    "noLib": true,
    "typeRoots": [
      "node_modules/@umbrik/webtutor-types/lib",
      "node_modules/@umbrik/webtutor-types/lib/xml"
    ]
  }
}
```