# Посмотри в окно

Проектная работа курса «Веб-разработчик» (Яндекс Практикум).  
Спринт 3/15 → Тема 13/14: Проектная работа → Урок 1/3.

## О проекте

«Посмотри в окно» — приложение, которое показывает подборку видео из разных городов в разное время суток.  
Задача проекта — **написать CSS для уже работающего приложения**, не меняя HTML-разметку, JavaScript и готовые стили компонентов (прелоадер, скроллбар, блок ошибки).

## Функциональность (реализована в script.js)

- При загрузке страницы скрипт получает данные из внешнего API, отрисовывает 5 карточек с видео и кнопку «Показать ещё».
- Адрес первого ролика подставляется в `<video>` в крупном блоке.
- Клик по карточке меняет текущее видео.
- Отправка формы ищет совпадения по городу и времени суток и перерисовывает страницу.
- При ошибках вместо видео показывается блок с сообщением.
- Во время загрузки в блоки видео и карточек подставляются прелоадеры.

> HTML, `script.js`, `preloader.css`, `error.css`, `fonts.css` менять нельзя.  
> Работа ведётся только в `styles/style.css`.

## Структура проекта

├── index.html
├── fonts/
│ ├── fonts.css
│ ├── Oswald-Bold.woff2
│ ├── Oswald-Bold.woff
│ ├── FiraSansCondensed-Regular.woff2
│ ├── FiraSansCondensed-Regular.woff
│ ├── FiraSansCondensed-Bold.woff2
│ └── FiraSansCondensed-Bold.woff
├── styles/
│ ├── style.css ← основной файл для доработки
│ ├── preloader.css ← готовый, не менять
│ └── error.css ← готовый, не менять
└── scripts/
└── script.js ← готовый, не менять


## Что сделано в style.css

### Шаг 1. Лейаут
- `.page` — flex-центрирование контента по горизонтали и вертикали.
- `.content` — flex-строка, элементы прижаты к низу (`align-items: flex-end`), заданы ширина и `gap`.
- `.search-form` — flex-строка с `justify-content: space-between` и `align-items: flex-start`.
- `.content__list-container` — фиксированная высота + `overflow: auto`.
- `.content__details` — `flex-grow: 1` и `gap` между заголовком и списком.

### Шаг 2. Размеры
- `.result__video-container` — фиксированные размеры, `margin-bottom`, `position: relative`.
- `.result__video` — `object-fit: cover` на всю ширину/высоту.
- `.content__list`, `.content__video-card` — `gap`, `align-items: flex-start`.
- `.content__video-card-thumbnail` — `min-width`, `height`, `object-fit`, `object-position`.
- `.content__video-card-description-container` — `flex-grow: 1`.

### Шаг 3. Тексты
- `.search-form__fieldset-title` — вес, размер, отступы.
- `.title` и `.content__accent` — шрифт Oswald, размер, цвет акцента.
- `.content__card-link` — блочный элемент, без подчёркивания, белый цвет.
- `.content__video-card-title` — `text-overflow: ellipsis`.
- `.content__video-card-description` — `line-height: 0.9` + `-webkit-line-clamp`.

### Шаг 4. Формы
- `.visually-hidden` — скрытие лейблов и браузерных чекбоксов.
- `.search-form__checkbox-list` — flex + `gap`.
- `.search-form__fieldset` — сброс `border`.
- `.search-form__label` — flex, `align-items: center`, `width: fit-content`, `gap`.
- `.search-form__textfield` — `appearance: none`, границы сверху/снизу, цвет текста и плейсхолдера, прозрачный фон.
- `.search-form__label:has(:focus-visible)` — обводка лейбла только при `:focus-visible`.
- `.search-form__pseudo-checkbox` + `::after` — кастомный чекбокс с `opacity`-переключением через `:checked`.
- Подчёркивание текста при наведении на весь лейбл.

### Шаг 5. Кнопки
- `.button` — общие стили (граница, цвет, шрифт, прозрачный фон, `cursor: pointer`).
- `.search-form__submit-button` — размер и `align-self: flex-end`.
- `.more-button` — `width: 100%`.
- Состояния `:hover`, `:active`, `:focus`, `:focus-visible`.

### Шаг 6. Состояния карточек
- `.content__card-link` — `display: block`.
- `.content__card-link_current`, `:active` — фон `#545050`.
- `:hover` — подчёркивание.
- `:focus` — сброс обводки, `:focus-visible` — `outline`.
- `.content__list-item` — `padding-inline: 3px`.

### Шаг 7. Кликабельность
- `cursor: pointer` на кнопках и ссылках карточек.

### Шаг 8. Прелоадеры
- `.result__video-container` и `.content__list-container` — `position: relative`, чтобы абсолютные прелоадеры и блок ошибки вставали внутрь них.

## Соответствие чек-листу

- ✅ Визуальное соответствие макету.
- ✅ Флекс-лейаут ключевых блоков, без лишнего абсолютного позиционирования.
- ✅ `position: absolute` — только у `.visually-hidden`.
- ✅ `object-fit` + `object-position` для медиа.
- ✅ Состояния чекбоксов через псевдоэлементы.
- ✅ Подчёркивание кнопок и чекбоксов на всю активную зону.
- ✅ `appearance: none` у текстового поля.
- ✅ `overflow: auto` вместо `scroll`.
- ✅ `gap` вместо `margin` для отступов между элементами.
- ✅ Состояния `:hover`, `:active`, `:focus`, `:focus-visible`.
- ✅ Аккуратное форматирование CSS, без дублей и пустых правил.

## Как запустить

1. Склонировать репозиторий.
2. Открыть `index.html` в браузере (Firefox, Google Chrome или Yandex Browser).
3. Для точной сверки с макетом — использовать плагин Pixel Perfect.

## Стек

- HTML5
- CSS3 (Flexbox, кастомные чекбоксы, `:has()`, `:focus-visible`, `object-fit`, `line-clamp`)
- JavaScript (готовый, без изменений)

## Автор

Учебный проект Яндекс Практикума.
