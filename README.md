# Контрольная работа №3 — `kr3-responsive-shop`

Тема: «Адаптивная вёрстка и доступность многостраничного HTML/CSS-сайта».

## Описание

Проект представляет собой адаптивную версию многостраничного HTML/CSS-сайта учебного магазина «Зачётка» (каталог учебных товаров). Работа выполнена **без Bootstrap** на основе проекта КР №1: адаптация выполняется вручную через медиазапросы, Flexbox, CSS Grid и responsive images.

## Практическая работа №12

Выполнено:

- создан отдельный репозиторий `kr3-responsive-shop`;
- перенесена основа проекта КР №1 (5 HTML-страниц, `css/style.css`, `js/main.js`, `images/`);
- добавлен файл `css/responsive.css` и подключён **после** `css/style.css` на всех страницах;
- на всех страницах проверен корректный `viewport` (`width=device-width, initial-scale=1.0`);
- применён подход **Mobile First**: базовые стили — мобильные, расширения — через `@media (min-width: ...)`;
- адаптирована шапка и навигация (burger-меню на мобильном, строка пунктов и sticky-шапка при `min-width: 768px`);
- адаптирован hero-блок (одна колонка на мобильном, две колонки при `min-width: 900px`, заголовок через `clamp()`);
- адаптирована сетка карточек товаров: 1 колонка → 2 (`640px`) → 3 (`1024px`) → 4 (`1280px`);
- адаптирована страница каталога: фильтр сверху на мобильном, боковая колонка 280px + sticky при `min-width: 1024px`;
- адаптированы изображения: `max-width: 100%`, `aspect-ratio` + `object-fit: cover`;
- использованы responsive images: `srcset` + `sizes` у карточки товара и галереи, `picture` с разными файлами hero (`hero-mobile/tablet/desktop.jpg`) и WebP-версией товара (`product-1.webp`);
- у изображений заданы `width`/`height` (нет скачка макета) и `loading="lazy"` ниже первого экрана;
- адаптирована форма заявки: одна колонка на мобильном, две колонки при `min-width: 768px`, поля `min-height: 44px`, широкие поля через `grid-column: 1 / -1`;
- адаптирована таблица характеристик: обёртка `.table-wrapper` с `overflow-x: auto`, у таблицы `min-width: 640px`;
- адаптировано модальное окно (`width: min(100% - 32px, 560px)`, прокрутка, `::backdrop`) и кнопка «Наверх»;
- выполнена проверка через DevTools на нескольких ширинах (см. ниже), горизонтального скролла нет.

## Проверенные ширины

- 360px (мобильный);
- 430px (крупный мобильный);
- 768px (планшет);
- 1024px (небольшой desktop);
- 1440px (широкий desktop).

Проверены все страницы: `index.html`, `catalog.html`, `product.html`, `order.html`, `contacts.html` — шапка, навигация, hero, карточки, таблица, форма, изображения, подвал, модальное окно. Responsive images проверены во вкладке Network (фильтр Img): на мобильной ширине загружаются файлы 480–640w, на desktop — 960w.

## Структура проекта

```text
kr3-responsive-shop/
├── index.html
├── catalog.html
├── product.html
├── order.html
├── contacts.html
├── css/
│   ├── style.css        # базовые стили (основа КР №1)
│   └── responsive.css   # адаптивные стили, Mobile First, медиазапросы min-width
├── js/
│   └── main.js          # burger-меню, модальное окно, формы, кнопка «Наверх»
├── images/              # hero-mobile/tablet/desktop, product-N-480/640/960, product-1.webp, ...
├── README.md
└── .gitignore
```

## Как запустить

Открыть `index.html` в браузере (или поднять любой статический сервер, например `npx serve .`).

## Как проверить адаптивность

1. Открыть страницу в браузере, включить DevTools → Device Toolbar (Ctrl+Shift+M).
2. Проверить ширины: 360, 430, 768, 1024, 1440px.
3. Убедиться, что нет горизонтального скролла (документ не шире вьюпорта).
4. Во вкладке Network (фильтр Img) проверить, какие файлы изображений загружаются на разных ширинах.

## Git: ветка, коммит, Pull Request

```bash
# новый репозиторий
git init
git add .
git commit -m "feat: base project from KR1"

# отдельная ветка под КР №3
git switch -c feature/responsive-layout

git add .
git commit -m "feat: add responsive layout styles"
git push -u origin feature/responsive-layout
```

Pull Request: `feature/responsive-layout` → `main`, заголовок «Add responsive layout styles», в описании — чек-лист выполненных пунктов и инструкция «Как проверить». После review — Merge Pull Request.
