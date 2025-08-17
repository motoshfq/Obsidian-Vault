# Модуль: Событие — item.js

Файл: `scripts/events/item.js`

Загрузка пары записей (`events`, `eventdetails`) по `id`, вычисление статуса и текущей/следующей активности, рендер всех секций страницы.

## Утилиты
- `$` — шорткат querySelector.
- `two(n)` — формат числа с ведущим нулём.
- `fmtRange(a,b)` — человекочитаемый диапазон дат.
- `splitLoc(loc)` — `{ main, extra }` из строки локации.
- `setText(el,v)`, `setHTML(el,v)` — безопасные помощники присвоения.

## Медиа/стримы
- `getYouTubeId(url)`, `getYouTubeEmbedSrc(url)` — извлечение ID и формирование `embed`‑URL с параметрами.
- `parseStreams(jsonLike)` — приводит поле трансляций к массиву `{ url, title }`.

## Данные
- `fetchEventAndDetails(id)` — параллельно тянет `events` и `eventdetails` (по `id`), отдаёт `{ ev, det }`.

## Рендер
- `renderTimeline(container, programJson)` — рендер программы по дням и пунктам.
- `renderChips(container, values)` — чипсы весовых/команды из CSV‑строки.
- Тело `main()` выставляет hero, лейблы (тип/категория/возраст), статус, «сейчас/ожидается», регламент, трансляции (iframe или список ссылок), контакты, адрес.

## Вычисления программы
- `parseProgram(json)` — JSON → массив дней.
- `computeNowNext(program)` — из расписания строит массив интервалов, возвращает `{ current, upcoming, context }`.

## Инициализация
- `main()` — оркестратор страницы; редирект на календарь при отсутствии данных.
- В конце файла вызывается `main()`.

— Навигация —
