---
layout: default
title: Использование
parent: Типы
nav_order: 2
---

## Использование

В процессе написания
{: .label .label-yellow }

### javascript

Можно использовать типы для проектов на _javascript_, используя jsdoc

Необходимо только [подключить типы]({% /docs/types/configuration %}#Установка) и можно использовать с помощью [деклараций jsdoc комментариев](https://www.typescriptlang.org/docs/handbook/jsdoc-supported-types.html).

```js
/** @type {ServerAgentDocument | null} serverAgentDocument */
var serverAgentDocument = tools.get_doc_by_key(
  "server_agent",
  "code",
  "Agent Code"
);
```

### typescript

Можно использовать типы для проектов на _typescript_

Необходимо только [подключить типы]({% /docs/types/configuration %}#Установка) и можно использовать как [типы typescript](https://www.typescriptlang.org/docs/handbook/typescript-from-scratch.html).

```typescript
var serverAgentDocument = tools.get_doc_by_key<ServerAgentDocument>(
  "server_agent",
  "code",
  "Agent Code"
);
```