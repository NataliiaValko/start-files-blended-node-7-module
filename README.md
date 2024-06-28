На цьому занятті вам потрібно створити документацію до вашого додатку для роботи з колекцією продуктів.

# TASK 1

1. Встановіть пакет `@redocly/cli` як Dev залежність:

```bash
npm install @redocly/cli --save-dev
```

2. Додайте в розділ із скриптами в `package.json` нові команди:

```json
{
  "scripts": {
    "build": "npm run build-docs",
    "build-docs": "redocly bundle --ext json -o docs/swagger.json",
    "preview-docs": "redocly preview-docs"
  }
}
```

3. Створіть файл `redocly.yaml` із таким вмістом:

```yaml
# See <https://redocly.com/docs/cli/configuration/> for more information.
apis:
  sample@v1:
    root: docs/openapi.yaml
extends:
  - recommended
rules:
  no-unused-components: error
theme:
  htmlTemplate: ./docs/index.html
  colors:
    primary:
      main: "#32329f"
  generateCodeSamples:
    languages:
      - lang: curl
      - lang: Node.js
      - lang: JavaScript
```

4. Створіть в корні проєкту папку `docs`, в ній створіть файл `index.html` із таким контентом:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>API Reference | ReDoc</title>
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <link rel="icon" type="image/png" href="favicon.png" />
    <style>
      body {
        margin: 0;
        padding: 0;
      }
    </style>
    {{{redocHead}}}
  </head>

  <body>
    {{{redocHTML}}}
  </body>
</html>
```

5. Створіть файл `docs/openapi.yaml` з наступним вмістом:

```yaml
openapi: 3.1.0
info:
  version: 1.0.0
  title: <назва вашого додатку>
  license:
    name: Apache 2.0
    url: http://www.apache.org/licenses/LICENSE-2.0.html
  description: >
    <опис вашого додатку>
tags:
  # теги, що ви будете використовувати
servers:
  - url: http://localhost:3000
  - url: #посилання на задеплоєний сайт
paths:
  # тут будуть посилання на ендпоінти
components:
  securitySchemes:
    bearerAuth:
      type: http
      scheme: bearer
```

Запустіть команду `npm run preview-docs`, щоб бачити внесені зміни.

6. Створіть папку `swagger`. У неї додайте папки `components` та `paths`. В папці `components` зберігайте частини сутностей, наприклад, опис відповідей або сутностей. В папці `paths` зберігайте файли документації відповідно до схеми побудови шляху. Наприклад, для роуту GET `/products/:productId` відповідним файлом буде /swagger/paths/products/{id}/get.yaml.

## TASK 2

Додайте документацію для роута `GET /products` у відповідний файл. У ній має бути:

1. tags - тег, до якого цей ендпоінт належить (Products)
2. summary - короткий опис ендпоінта
3. operationId - унікальний ідентифікатор операції
4. description - більш розгорнутий опис
5. security - зазначте, що ми використовуємо авторизацію за допомогою Bearer токену
6. responses - варіанти відповідей для статусів:
   - 200
   - 401
   - 500

Додайте посилання на цей ендпоінт до файлу `./docs/openapi.yaml`.

## TASK 3

Додайте документацію для роута `GET /products/:productId` у відповідний файл. У ній має бути:

1. tags - тег, до якого цей ендпоінт належить (Products)
2. summary - короткий опис ендпоінта
3. operationId - унікальний ідентифікатор операції
4. description - більш розгорнутий опис
5. security - зазначте, що ми використовуємо авторизацію за допомогою Bearer токену
6. parameters - параметри запиту (для цього ендпоінту - параметр шляху `:productId`)
7. responses - варіанти відповідей для статусів:
   - 200
   - 401
   - 404
   - 500

Додайте посилання на цей ендпоінт до файлу `./docs/openapi.yaml`.

## TASK 4

Додайте документацію для роута `POST /products` у відповідний файл. У ній має бути:

1. tags – тег, до якого цей ендпоінт належить (Products)
2. summary – короткий опис ендпоінта
3. operationId – унікальний ідентифікатор операції
4. description – більш розгорнутий опис
5. security – зазначте, що ми використовуємо авторизацію за допомогою Bearer токену
6. requestBody – тіло запиту, що містить дані для створення нового продукту
7. responses – варіанти відповідей для статусів:
   - 201
   - 400
   - 401
   - 500

Додайте посилання на цей ендпоінт до файлу `./docs/openapi.yaml`.

## TASK 5

Додайте документацію для роута `PATCH /products/:productId` у відповідний файл. У ній має бути:

1. tags – тег, до якого цей ендпоінт належить (Products)
2. summary – короткий опис ендпоінта
3. operationId – унікальний ідентифікатор операції
4. description – більш розгорнутий опис
5. security – зазначте, що ми використовуємо авторизацію за допомогою Bearer токену
6. parameters – параметри запиту (для цього ендпоінту – параметр шляху `:productId`)
7. requestBody – тіло запиту, що містить дані для оновлення продукту
8. responses – варіанти відповідей для статусів:
   - 200
   - 400
   - 401
   - 404
   - 500

Додайте посилання на цей ендпоінт до файлу `./docs/openapi.yaml`.

## TASK 6

Додайте документацію для роута `DELETE /products/:productId` у відповідний файл. У ній має бути:

1. tags – тег, до якого цей ендпоінт належить (Products)
2. summary – короткий опис ендпоінта
3. operationId – унікальний ідентифікатор операції
4. description – більш розгорнутий опис
5. security – зазначте, що ми використовуємо авторизацію за допомогою Bearer токену
6. parameters – параметри запиту (для цього ендпоінту – параметр шляху `:productId`)
7. responses – варіанти відповідей для статусів:
   - 200
   - 401
   - 404
   - 500

Додайте посилання на цей ендпоінт до файлу `./docs/openapi.yaml`.
