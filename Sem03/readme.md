# CSS 

## Какво е CSS
**HTML** описва съдържанието, а **CSS** описва визуализацията: подредба, размери, цветове на текст и фон и др.

---

## Как работи CSS
Избираме елементи чрез **селектори** и задаваме стойности на **properties**.  
Браузърът прилага тези стойности върху всички елементи, които пасват на селектора.

---

## CSS синтаксис
```css
selector {
  property: value;
  /* ... */
}
```

## Начини за включване на CSS

- Inline (в style атрибут) – не се препоръчва
  
```css
<a href="//google.com" style="color:red">Click Here</a>
```

- Вграден стил в <style> (в <head>) – по-рядко използван

```css
<style>
  a { color: red }
</style>
```

- Външен файл – най-добрият вариант

```css
<link href="style.css" rel="stylesheet">
```

---

## Основни селектори
| Селектор       | Описание                |
| -------------- | ----------------------- |
| `*`            | Всички елементи         |
| `foo`          | По HTML таг             |
| `.bar`         | По клас                 |
| `#baz`         | По `id`                 |
| `foo bar`      | Наследници (descendant) |
| `foo, bar`     | Обединение на селектори |
| `tag#id.class` | Комбиниран селектор     |


## Комбиниране и допълнителни селектори

- `foo > bar` – директни наследници

- `foo + bar` – непосредствен следващ sibling

- `E:first-child` – първи наследник

- `E:hover` – при задържане на мишката

## Цветове

| Метод     | Пример                 |
| --------- | ---------------------- |
| Име       | `red`                  |
| RGB       | `rgb(255, 0, 0)`       |
| HEX       | `#ff0000` или `#f00`   |
| HSL       | `hsl(0, 100%, 50%)`    |
| RGBA/HSLA | `rgba(255, 0, 0, 0.5)` |


## Единици и метрики
- `px` – пиксели

- `pt` – точки (не за уеб)

- `em` – относително спрямо текущия шрифт

- `%` – спрямо родителя

## Текст и шрифтове

### Текст:

```css
color: red;
text-decoration: underline;
text-align: center;
text-transform: uppercase;
```


### Шрифтове:

```css
font-style: italic;
font-weight: bold;
font-size: 16px;
line-height: 30px;
font-family: "Verdana", "Consolas", sans-serif;
```

### Съкратено:

```css
font: italic bold 16px/30px Verdana, Consolas, sans-serif;
```


## Фон (Background)
```css
background-color: #fafafa;
background-image: url("pattern.png");
background-repeat: repeat-x;
background-position: center;
background-attachment: fixed;
```


### Съкратено:
```css
background: #fafafa url("pattern.png") center repeat-x fixed; 
```

## Display

| Стойност               | Поведение                |
| ---------------------- | ------------------------ |
| `none`                 | Скрива елемента          |
| `inline`               | На един ред (като текст) |
| `block`                | Отделен блок             |
| `inline-block`         | Комбинира двата          |
| `table` / `table-cell` | Имитация на таблица      |
| `flex`, `grid`         | Модерни layout-и (CSS2+) |


## Box Model
```lua
+---------------------------+
|        margin             |
|  +---------------------+  |
|  |      border         |  |
|  |  +---------------+  |  |
|  |  |   padding     |  |  |
|  |  |  +---------+  |  |  |
|  |  |  | content |  |  |  |
|  |  |  +---------+  |  |  |
|  |  +---------------+  |  |
|  +---------------------+  |
+---------------------------+
```

## Position

| Стойност   | Описание                                |
| ---------- | --------------------------------------- |
| `static`   | По подразбиране                         |
| `relative` | Отместване спрямо оригиналното място    |
| `absolute` | Спрямо най-близкия позициониран родител |
| `fixed`    | Спрямо прозореца на браузъра            |


## Други полезни свойства

- `z-index` – подредба по дълбочина

- `opacity` – прозрачност

- `visibility` – скрит, но запазва място

- `overflow` – visible | hidden | scroll | auto

---
### CSS Flexbox and Grid Guides

[**Flexbox**](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

[**Grid**](https://css-tricks.com/snippets/css/complete-guide-grid/)


---
## Задачи

### Задача 1: Основни селектори
Създай HTML страница с няколко параграфа и бутони.  
Напиши CSS, така че:
- Всички параграфи да са с шрифт *Verdana* и цвят **син**;
- Само параграфът с клас `.important` да е **удебелен** и **червен**;
- Бутоните (`<button>`) да имат зелен фон и бял текст.

💡 *Подсказка:* използвай селектори по **таг**, **клас** и **елемент**.

---

### Задача 2: Box Model
Направи трите блока да изглеждат като кутии с вътрешен и външен отстъп:
```html
<div class="box red"></div>
<div class="box green"></div>
<div class="box blue"></div>
```
Изисквания:

- `.box` има размер 100x100px;

- Разстояние между кутиите: 20px;

- Всяка има различен фон;

- Добави `border` и `padding`.

Подсказка: използвай `margin`, `padding`, `border` и `background-color`.

### Задача 3: Позициониране
Създай елемент с текст „Hello, world!“ и го постави:

- в горния десен ъгъл на страницата с `position: fixed`;

- с отстояние 10px от ръбовете;

- с полупрозрачен фон.

Подсказка: `position: fixed`; `top: 10px`; `right: 10px`; `opacity: 0.8`;


### Задача 4: Каре с изображение и текст
Направи „картичка“:

```html
<div class="card">
  <img src="photo.jpg" alt="example">
  <h3>Title</h3>
  <p>Description text...</p>
</div>
```
Изисквания:

- Сянка (`box-shadow`);

- Закръглени ръбове (`border-radius`);

- Центриране в страницата (`margin: auto; width: 300px`;);

- Текстът е подравнен по центъра.

Подсказка: комбинирай `display`, `text-align`, `box-shadow`, `border-radius`.

### Задача 5: Мини проект — Визитка

Създай визитка с име, позиция, снимка и контактни данни.
Използвай:

- `display: flex`; за подредба;

- `background`, `border-radius`, `box-shadow`;

- различни цветове и шрифтове;

- ефект при задържане с `transform: scale(1.05)`.

Подсказка: комбинирай всичко научено дотук.

