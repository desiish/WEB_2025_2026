# HTML Forms

## 1. Основна идея

HTML формите служат за събиране на данни от потребителя и изпращането им към сървъра.
Основният контейнер е `<form>`, който включва полета (`<input>`, `<select>`, `<textarea>`), бутони и т.н.

```html
<form method="post" action="/add-course.php">
  <label for="course-title">Course Title</label>
  <input id="course-title" name="title" required>
  <button type="submit">Submit</button>
</form>
```


| Атрибут   | Описание                                                   | Пример                                 |
| --------- | ---------------------------------------------------------- | -------------------------------------- |
| `action`  | URL адресът, където се изпращат данните                    | `<form action="/save.php">`            |
| `method`  | HTTP метод: `get` или `post`                               | `<form method="post">`                 |
| `enctype` | Кодировка при изпращане на файлове (`multipart/form-data`) | `<form enctype="multipart/form-data">` |



## 2. Основни тагове

| Таг          | Описание                      | Пример                                                                       |
| ------------ | ----------------------------- | ---------------------------------------------------------------------------- |
| `<form>`     | Определя формата              | `<form action="/send" method="post"></form>`                                 |
| `<input>`    | Едноредово поле за въвеждане  | `<input type="text" name="user">`                                            |
| `<label>`    | Етикет за поле                | `<label for="user">User</label>`                                             |
| `<textarea>` | Много редове текст            | `<textarea name="message"></textarea>`                                       |
| `<fieldset>` | Групира елементи от формата   | `<fieldset>...</fieldset>`                                                   |
| `<legend>`   | Заглавие на `<fieldset>`      | `<legend>Personal Info</legend>`                                             |
| `<button>`   | Бутон за действие             | `<button type="submit">Send</button>`                                        |
| `<select>`   | Падащо меню                   | `<select><option>...</option></select>`                                      |
| `<option>`   | Елемент от меню               | `<option value="bg">Bulgaria</option>`                                       |
| `<optgroup>` | Група от опции                | `<optgroup label="Europe">...</optgroup>`                                    |
| `<datalist>` | Автодовършване (autocomplete) | `<input list="cities"><datalist id="cities"><option>...</option></datalist>` |


## 3. Атрибути на `<input>`

| Атрибут       | Значение                                | Пример                                                          |
| ------------- | --------------------------------------- | --------------------------------------------------------------- |
| `type`        | Определя вида на полето                 |`text`, `password`, `email`, `number`, `date`, `color`, `range`, `checkbox`, `radio`, `file`, `submit`, `reset`, `url`, `tel`, `search`|
| `name`        | Ключ, под който стойността се изпраща   | `<input name="email">`                                          |
| `id`          | Уникален идентификатор (за `label for`) | `<input id="email">`                                            |
| `placeholder` | Подсказваща стойност                    | `<input placeholder="Enter name">`                              |
| `required`    | Задължително поле                       | `<input required>`                                              |
| `disabled`    | Изключено поле                          | `<input disabled>`                                              |
| `pattern`     | Регулярен израз (валидация)             | `<input pattern="[A-Za-z]{3,}">`                                |
| `value`       | Начална стойност                        | `<input value="Мy name">`                                       |
| `checked`     | Отметка по подразбиране                 | `<input type="checkbox" checked>`                               |


## 4. Пример

```html
<form method="post" action="/submit">
  <label>Username <input type="text" name="username" placeholder="John Smith" required></label>
  <label>Password <input type="password" name="password" required></label>
  <label>Email <input type="email" name="email" placeholder="a@a.com"></label>

  <p>Gender</p>
  <label><input type="radio" name="gender" value="M"> Male</label>
  <label><input type="radio" name="gender" value="F"> Female</label>

  <fieldset>
    <legend>Favorite things</legend>
    <label>Number <input type="number" min="0" max="10"></label>
    <label>Color <input type="color"></label>
  </fieldset>

  <label for="browser">Browser</label>
  <input list="browsers-list" id="browser" name="browser">
  <datalist id="browsers-list">
    <option value="Firefox">
    <option value="Chrome">
  </datalist>

  <p>Age group:</p>
  <select name="age">
    <optgroup label="Young">
      <option value="1">Kid (0-12)</option>
      <option value="2">Teen (13-19)</option>
    </optgroup>
    <option value="3" selected>Adult (20+)</option>
  </select>

  <br><br>
  <button type="submit">Submit</button>
  <button type="reset">Clear</button>
</form>
```

## 5. DOM — Document Object Model
Какво е DOM?

DOM (Document Object Model) е дървовидно представяне на HTML документа, което позволява на JavaScript да достъпва, променя и създава елементи динамично.

Всеки HTML елемент е възел (node) в дървото.

Връзките са родител–дете (parent–child).

Можем да променяме съдържание, стилове и атрибути чрез JS.

```html
<html>
  <body>
    <h1>Hello</h1>
    <p>Welcome to DOM</p>
  </body>
</html>
```

```
Document
 └── html
      └── body
           ├── h1
           │    └── "Hello"
           └── p
                └── "Welcome to DOM"

```

### Методи за достъпване на елементи от DOM дървото 

| Метод                                    | Описание                             | Пример                                    |
| ---------------------------------------- | ------------------------------------ | ----------------------------------------- |
| `document.getElementById(id)`            | Намира елемент по `id`               | `document.getElementById("title")`        |
| `document.getElementsByClassName(class)` | Връща HTMLCollection по клас         | `document.getElementsByClassName("item")` |
| `document.getElementsByTagName(tag)`     | Връща елементи по таг                | `document.getElementsByTagName("div")`    |
| `document.querySelector(selector)`       | Връща първия елемент по CSS селектор | `document.querySelector(".btn")`          |
| `document.querySelectorAll(selector)`    | Връща всички по селектор (NodeList)  | `document.querySelectorAll("p")`          |


---
## Задачи

### Задача 1:

Създай форма за добавяне на избираема дисциплина с:

- Име на предмета — задължително, max 150 символа
- Преподавател — задължително, max 200 символа
- Описание — задължително, min 10 символа
- Група — една измежду М, ПМ, ОКН и ЯКН
- Кредити — цяло положително число

### Задача 2:

Направи форма за регистрация, която включва:
- Username (minlength 3)
- Password (minlength 8)
- Email (валиден формат)
- Снимка на профила
- Checkbox „Съгласен съм с условията“
- Submit бутон

### Задача 3:

Създай форма за обратна връзка (feedback):
- Name
- Email
- Subject (dropdown)
- Message (textarea)
- Rating (range от 1 до 5)
- Submit бутон
