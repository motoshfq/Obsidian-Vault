# Модуль: Новости — index.js

Файл: `scripts/news/index.js`

Загрузка списка новостей из Supabase, поддержка категорий, поиска, тегов (в UI скрыты), пагинации, тёплый кеш.

## Константы и состояние
- `CATEGORY_MAP` — словарь ключ → человекочитаемая категория.
- `PAGE_SIZE = 8` — размер страницы.
- `state` — `{ category, tag, search, page }`, инициализируется из `location.search`.

## Утилиты
- `setState(patch)` — мержит состояние и синхронизирует URL (`history.replaceState`).
- `$`, `$all` — шорткаты querySelector/All.
- `formatDate(iso)` — локализованная дата `uk-UA`.

## Рендер
- `renderCategories(container)` — строит пилюли категорий с обработчиками.
- `renderTags(container, items)` — сейчас скрыт по требованию (задаёт `hidden`).
- `renderEmpty(container, isError)` — карточка «пусто» или «ошибка» с кнопкой «Попробовать ещё раз».
- `renderList(container, items)` — карточки новостей: медиа, бейдж, заголовок, мета (дата, автор, чтение), теги (до 4), выжимка, кнопка.
- `renderPagination(container, totalCount)` — кнопки навигации, активная страница, расчёт количества страниц.

## Данные
- `fetchNewsPage()`:
  - Формирует `eq` по категории, сортирует по `publishedAt desc`, запрашивает `PAGE_SIZE` с оффсетом.
  - Клиентская фильтрация по `search` и `tag`.
  - Возвращает `{ items, totalApprox, error }` (approx для построения пагинации без «count(*)»).

## UI
- `bindUI()` — debounce‑поиск и очистка.
- `fetchAndRender()` — orchestrator: категории, спиннер, загрузка данных, рендер списка/пагинации/тегов.
- `ensureContainers()` — если контейнеров нет в DOM, создаёт их (идемпотентно).
- `warmupCache(limit=120)` — прогревает `window.__newsCache` для быстрых блоков «схожие/последние».

## Инициализация
- `initPage(root=document)` — ensure → bind → fetch → warmup.
- `window.addEventListener('DOMContentLoaded', initPage)` — прогрессивная автоинициализация.

— Навигация —]]
