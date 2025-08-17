# Модуль: Главная — events.js (upcoming)

Файл: `scripts/home/events.js`

Выборка ближайших событий и рендер 3 карточек + заполнение HeroCard.

## Утилиты и словари
- `$`, `el(tag, cls)`, `two(n)` — базовые помощники DOM/формата.
- `trimText(t, len)` — усечение строк.
- Формататоры: `fmtDowTime(date)`, `fmtDateRange(a,b)`.
- Справочники: `STATUS_LABELS`, `TYPE_LABELS`, `CATEGORY_LABELS`, `AGE_LABELS`.
- `labelize(key, dict)` — безопасное получение подписи.

## Данные
- `fetchUpcoming(limit=3)` — события с `date >= today` по возрастанию даты (через `customQuery`).

## Рендер
- `updateHero(ev)` — подставляет главное событие в HeroCard (картинка, заголовок, город/дата/время, чипсы), кликабельный переход на детали.
- `renderGrid(list)` — карточки событий для секции «Найближчі події».

## Инициализация
- `initPage(root)` — грузит, обновляет Hero, рендерит грид; graceful fallback на сообщения.
- В конце файла вызывается `initPage()`.

— Навигация —