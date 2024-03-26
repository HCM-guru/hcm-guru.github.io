---
layout: default
title: Конфигурация
parent: Типы
nav_order: 1
---

## Конфигурация

В процессе написания
{: .label .label-yellow }

Типы доступны в проектах как для _typescript_, так и для проекты на javascript

Для работы типов необходимо установить _typescript_

```bash
npm i typescript@4.4.4
```

Далее необходимо установить зависимость с типами

```bash
npm i @umbrik/webtutor-types
```

После этого необходимо сгенерировать _tsconfig.json_

Генерируем конфиг, либо просто создаем вручную файл tsconfig.json

```bash
npx tsc -init
```

Далее добавляем/обновляем _tsconfig_

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
    // отключение автоматической загрузки любых типов/библиотек
    "noLib": true,
    // типы для WebSoft HCM
    "typeRoots": [
      "node_modules/@umbrik/webtutor-types/lib",
      "node_modules/@umbrik/webtutor-types/lib/xml"
    ]
  }
}
```