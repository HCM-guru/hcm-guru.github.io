---
layout: default
title: FAQ
nav_order: 4
---
# FAQ

## Typescript

### Почему версия 4.4.4?

Для того, чтобы можно было без дополнительных сложностей транспилировать ваш код на _typescript_ в код для WebSoft HCM мы рекомендуем использовать _typescript_ 4.4.4 версии.

Причина в [изменении](https://github.com/microsoft/TypeScript/pull/45304) конкатенации [_шаблонных строк_](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals) с **+** на **.concat** в _typescript_ 4.5 и отсутствии данного метода в WebSoft HCM.


{: .note }
Да, можно использовать _typescript_ версией выше, чем 4.4.4, но для этого потребуется дополнительная обработка (например, ковертация конкатенаций строк с использованием _esbuild_ или _webpack_).