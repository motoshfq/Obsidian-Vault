# API слой — api.js

Файл: `scripts/lib/api.js`

Тонкий клиент для Supabase REST (PostgREST) из браузера без сборщика.

## Конфигурация
- `SUPABASE_URL`, `SUPABASE_ANON_KEY` — публичные настройки фронтенда.
- `ensureConfig()` — валидирует наличие конфигурации; кидает ошибку, если не заданы.

## Низкоуровневые утилиты
- `buildQuery({ select, eq = {}, order, limit, offset })`:
  - Формирует query‑строку PostgREST. Фильтры `eq`: `column=eq.value`.

## CRUD
- `api.get({ table, select='*', eq={}, order, limit, offset, signal, customQuery })`:
  - GET к `/rest/v1/<table>?<query>`. Возвращает JSON‑массив.
- `api.insert({ table, rows })`:
  - POST, `Prefer: return=representation`. Возвращает вставленные строки.
- `api.update({ table, values, eq })`:
  - PATCH по фильтру `eq`. Возвращает обновлённые строки.
- `api.delete({ table, eq })`:
  - DELETE по фильтру `eq`. Возвращает `true` при успехе.

## Хелперы
- `selectColumns(table, columns=['*'], options={})`:
  - Сокращение над `api.get` для выборки колонок.

## Ошибки и безопасность
- Все методы при `!res.ok` читают текст ответа и бросают подробное исключение.
- Ключ анонима только публичный; приватные операции не выполняются на фронтенде.

## Использование в проекте
- Используется модулями страниц для загрузки данных.

— Навигация —
