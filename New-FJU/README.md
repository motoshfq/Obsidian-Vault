# Документация проекта FJU

Эта ветка заметок описывает фронтенд-проект (статический сайт) Федерации Дзюдо Украины: страницы, модули, компоненты, маршрутизацию и доступ к данным.

## Навигация
- Архитектура
- Роутер — router.js
- API слой — api.js

### Страницы
- Страницы/Главная
- Страницы/Новости
- Страницы/Новость
- Страницы/Календарь
- Страницы/Событие — детали

### Модули (JS)
- Модули/Новости/index.js — список новостей, фильтры, пагинация
- Модули/Новости/item.js — страница одной новости
- Модули/Новости/home-news.js — блок «Останні новини» на главной
- Модули/Календарь/index.js — страница календаря подій
- Модули/События/item.js — страница деталей события
- Модули/Домашняя/events.js — блок ближайших событий на главной

### Компоненты (UI)
- Компоненты/header.js — мобильное меню/бургер-дровер

### Данные и ассеты
- Источник данных: Supabase REST (таблицы: `news`, `events`, `eventdetails`)
- Медиа и статические файлы: папка `assets/`

## Быстрый обзор
- Без сборщика: ES-модули напрямую в браузере, progressive enhancement.
- Лёгкий SPA-роутер (замена только тега `<main>` при переходах между страницами).
- Новостной раздел, календарь, страница события, общий заголовок/футер.

## Маршрут чтения
1. Архитектура
2. Роутер — router.js
3. API слой — api.js
4. Страницы/Главная
5. Модули/Домашняя/events.js
6. Модули/Новости/home-news.js
7. Страницы/Новости
8. Модули/Новости/index.js
9. Страницы/Новость
10. Модули/Новости/item.js
11. Страницы/Календарь
12. Модули/Календарь/index.js
13. Страницы/Событие — детали
14. Модули/События/item.js
15. Компоненты/header.js

— Навигация —


## Связи (карта)
Readme
↳ Архитектура
  ↳ Страницы
    ↳ Страницы/Главная (index)
       ↳ HTML: `index.html`
       ↳ CSS:
         - `css/common.css`
         - `css/components/header.css`
         - `css/components/header--responsive.css`
         - `css/components/drawer.css`
         - `css/pages/home/hero.css`
         - `css/pages/home/about.css`
         - `css/pages/home/news.css`
         - `css/pages/home/events.css`
         - `css/pages/home/partners.css`
         - `css/news/index/typography.css`
         - `css/components/footer.css`
       ↳ JS:
         - `scripts/news/home-news.js`
         - `scripts/home/events.js`
         - `scripts/components/header.js`
    ↳ Страницы/Новости
       ↳ HTML: `news.html`
       ↳ CSS:
         - `css/common.css`
         - `css/components/footer.css`
         - `css/components/header.css`
         - `css/components/header--responsive.css`
         - `css/components/drawer.css`
         - `css/news/index/base.css`
         - `css/news/index/card.css`
         - `css/news/index/typography.css`
       ↳ JS:
         - `scripts/news/index.js`
         - `scripts/lib/router.js`
         - `scripts/components/header.js`
    ↳ Страницы/Новость
       ↳ HTML: `news-item.html`
       ↳ CSS:
         - `css/common.css`
         - `css/components/header.css`
         - `css/components/header--responsive.css`
         - `css/components/drawer.css`
         - `css/news/item/base.css`
         - `css/news/item/typography.css`
         - `css/news/item/breadcrumbs.css`
         - `css/components/footer.css`
       ↳ JS:
         - `scripts/news/item.js`
         - `scripts/lib/router.js`
         - `scripts/components/header.js`
    ↳Страницы/Календарь
       ↳ HTML: `calendar.html`
       ↳ CSS:
         - `css/common.css`
         - `css/components/footer.css`
         - `css/components/header.css`
         - `css/components/header--responsive.css`
         - `css/components/drawer.css`
         - `css/pages/calendar/base.css`
         - `css/pages/calendar/filters.css`
         - `css/pages/calendar/list.css`
       ↳ JS:
         - `scripts/calendar/index.js`
         - `scripts/lib/router.js`
         - `scripts/components/header.js`
    ↳ Страницы/Событие — детали
       ↳ HTML: `event.html`
       ↳ CSS:
         - `css/common.css`
         - `css/components/header.css`
         - `css/components/header--responsive.css`
         - `css/components/drawer.css`
         - `css/events/item/base.css`
         - `css/components/footer.css`
       ↳ JS:
         - `scripts/events/item.js`
         - `scripts/lib/router.js`
         - `scripts/components/header.js`
  ↳ Компоненты
    ↳ Компоненты/header.js]]
       ↳ CSS:
         - `css/components/header.css`
         - `css/components/header--responsive.css`
         - `css/components/drawer.css`
       ↳ JS:
         - `scripts/components/header.js`
  ↳ HTML
    - HTML/index.html
    - HTML/news.html
    - HTML/news-item.html
    - HTML/calendar.html
    - HTML/event.html
  ↳ CSS
    - CSS/common.css
    - CSS/components/header.css
    - CSS/components/header--responsive.css
    - CSS/components/drawer.css
    - CSS/components/footer.css
    - CSS/pages/home/hero.css
    - CSS/pages/home/about.css
    - CSS/pages/home/news.css
    - CSS/pages/home/events.css
    - CSS/pages/home/partners.css
    - CSS/news/index/base.css
    - CSS/news/index/card.css
    - CSS/news/index/typography.css
    - CSS/news/item/base.css
    - CSS/news/item/typography.css
    - CSS/news/item/breadcrumbs.css
    - CSS/pages/calendar/base.css
    - CSS/pages/calendar/filters.css
    - CSS/pages/calendar/list.css
    - CSS/events/item/base.css 