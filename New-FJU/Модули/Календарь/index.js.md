# Модуль: Календарь — index.js

Файл: `scripts/calendar/index.js`

Загрузка событий за выбранный месяц с учётом перекрытия интервалов, фильтры, рендер карточек, подсчёт количества.

## Справочники и состояние
- `TYPE_LABELS`, `CATEGORY_LABELS`, `STATUS_LABELS`, `AGE_LABELS` — словари для лейблов.
- `state` — `{ q, type, category, status, age }` — значения фильтров.
- `currentYear`, `currentMonthIndex` — выбранный месяц.
- `monthCache: Map<YYYY-MM, events[]>` — кеш выборок по месяцам.

## Утилиты дат/формата
- `$` — шорткат querySelector.
- `fmtDateReadable(iso)` — `{ day, month, year }` для метки.
- `daySpan(a,b)` — длительность в днях.
- `two(n)` — дополнение нулями.
- `getDateLines(startISO, endISO)` — строки для бэйджа даты (верх/низ).
- `getFullBadgeText(startISO, endISO)` — компактная форма `DD.MM по DD.MM`.
- `ymdLocal(d)` — локальная дата `YYYY-MM-DD`.
- `firstDayOfMonthISO(year, monthIndex)`, `lastDayOfMonthISO(year, monthIndex)` — границы месяца.

## Вычисления и фильтры
- `computeStatus(ev)` — planned/ongoing/finished/canceled на основе текущей даты.
- `bindFilters()` — привязка UI к `state`, кнопка «Сброс».
- `matchesFilters(ev)` — проверяет совпадение по тексту/типу/категории/статусу/возрасту.
- `updateMonthLabel()` — подпись текущего месяца в шапке.

## Данные
- `fetchEventsForMonth(year, monthIndex)` — получает события, пересекающие выбранный месяц. Делает OR-запрос по `date`/`endDate`, затем клиентом строго фильтрует по интервалу; кеширует результат.
- `fetchEventDetailsIdsForMonth(year, monthIndex)` — получает множество `id` из `eventdetails` (для подсветки наличия «Деталі»).

## Рендер
- `renderList(list)` — строит карточки событий: дата‑бейдж, лейблы (тип/категория/статус/возраст), описание, ссылки (регламент, деталі).
- `updateEventsCount(count)` — счётчик в заголовке страницы.

## Инициализация и поток
- `populateMonthYearSelectors()` — заполняет селекты, обработчики изменения.
- `fetchAndRender()` — параллельно получает `events` и `eventdetails` id‑set, фильтрует, рендерит список.
- `init()` — связывает всё вместе: фильтры, кнопки навигации по месяцам, «Сегодня», первичный рендер.
- В конце файла вызывается `init()`.

## Импорт из CSV (локально)
- `maybeBootstrapFromCSVIfEmpty()` — только на `localhost`: если таблица пуста, пытается прочитать `assets/events.csv` и залить батчами через `api.insert`.
- `parseCsv(text)` + `splitCsvLine(line)` — простой парсер CSV.
- `parseLocationParts(loc)` — евристическое разбиение «город, остальное».

— Навигация —