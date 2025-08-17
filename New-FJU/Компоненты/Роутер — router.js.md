# Роутер — router.js

Файл: `scripts/lib/router.js`

Лёгкий SPA-роутер. Меняет только `<main>`, управляет стилями `<link rel="stylesheet">`, обрабатывает hash-якоря, навигацию назад/вперёд, инициализирует скрипты конкретной страницы.

## Основной поток
- `attach()` — точка входа: помечает текущие стили как управляемые роутером, вешает обработчики `click`/`popstate`, вызывает `initForPage(document)` и скроллит к `#hash` при первой загрузке.
- При клике по ссылке: `onClick(e)` → `allowed(a)` → `fetchPage()` → `ensureStyles()` → `history.pushState()` → `fadeSwapMain()` → `initForPage(newMain)`.
- При `popstate`: `onPop()` делает `fetchPage()` и `fadeSwapMain()` без `pushState`.

## Функции
- `allowed(a)`:
  - Пропускает только ссылки того же origin, на `.html` (не только `#hash`), без `target="_blank"/download`.
- `normalizeKey(href)`:
  - Нормализует URL (обнуляет `hash` и `search`) для сравнения и ключей стилей.
- `scrollToHash(root)`:
  - Плавно скроллит к элементу `id` или `[name]` из текущего `location.hash`.
- `fetchPage(url)`:
  - Загружает HTML, парсит DOM, возвращает `{ title, main, styles }` — заголовок, найденный `<main>`, и список стилей.
- `fadeSwapMain(newMain)`:
  - Плавная замена `<main>` (opacity → replace → opacity up), вызывает `initForPage(newMain)`, обновляет ключ пути `lastPathKey`, скроллит к якорю.
- `ensureStyles(urls)`:
  - Сопоставляет существующие `<link rel="stylesheet">` с необходимыми, удаляет лишние (router-managed), догружает недостающие, использует `dataset.styleKey`.
- `initForPage(root)`:
  - По `location.pathname` лениво импортирует нужный модуль:
    - `/news.html` → `../news/index.js` (`initPage`)
    - `/news-item.html` → `../news/item.js` (`initPage`)
    - `/calendar.html` → `../calendar/index.js`
    - `/event.html` → `../events/item.js`
    - `/index.html` → параллельно `../home/events.js` и `../news/home-news.js`
- `onClick(e)`:
  - Перехватывает клики по ссылкам; отдельная обработка якорей на той же странице (плавный скролл без refetch). При межстраничной навигации — SPA‑подмена.
- `onPop()`:
  - Обрабатывает переходы назад/вперёд. Если изменился только `hash`, то просто скроллит; иначе — догружает страницу и подменяет `<main>`.
- `attach()`:
  - Инициализация: пометка стилей, обработчики событий, первичный `initForPage`, авто‑attach по `DOMContentLoaded`.

## Особенности
- Progressive enhancement: при ошибках всегда откат к обычной навигации (`location.href = ...`).
- Управление стилями: страница может требовать свои CSS; роутер удаляет/добавляет их прозрачно.
- Якоря: плавный скролл при переходах вида `...#section` внутри той же страницы без refetch.

— Навигация —
