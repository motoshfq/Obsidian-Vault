# Модуль: Главная — home-news.js

Файл: `scripts/news/home-news.js`

Рендер блока «Останні новини» на главной.

## Функции
- `$`, `formatDate(iso)` — утилиты.
- `renderHomeNews(container, items)` — грид карточек новостей (бейдж категории, картинка, дата, заголовок, выжимка, стрелка).
- `loadHomeNews(root=document)` — находит секцию `section#news .container`, ставит спиннер, запрашивает 12 записей (`id,title,category,publishedAt,image_url,excerpt`), рендерит 6.
- `initPage(root)` — вызов `loadHomeNews`.
- Автозапуск: по `DOMContentLoaded` или отложенный `setTimeout` (если скрипт вставлен поздно).

— Навигация —