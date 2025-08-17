# Модуль: Новости — item.js

Файл: `scripts/news/item.js`

Загрузка и показ одной новости, обработка тегов, шаринг, связанные и последние новости, лайткоробка (lightbox) для изображений.

## Утилиты
- `$` — шорткат querySelector.
- `formatDate(iso)` — формат даты `uk-UA`.
- `sanitize(html)` — удаляет `<script>`, inline‑обработчики и `javascript:` из контента.
- `countWords(text)` — считает слова для оценки времени чтения.
- `truncate(text, max)` — усечение заголовков в хлебных крошках.

## Данные
- `fetchArticleById(articleId)` — стратегический поиск статьи:
  1) точный `id`, 2) `slug`, 3) клиентский поиск в первых 100 записях.
- `normalizeArticle(raw)` — выравнивает структуру: `hero {src,alt}`, `author`, `tags[]` (строка → JSON → массив), `publishedAt` и пр.

## Рендер
- `renderTags(tags)` — строит ряд кнопок‑тегов; клик ведёт на `news.html?tag=...`.
- `renderBreadcrumbs(article)` — «Новини» → категория (если есть) → обрезанный заголовок.
- `renderMiniCards(container, items)` — мини‑карточки для блоков «Схожі/Останні».
- `renderArticle(article)` — заполняет title, category, date, author, время чтения, hero с fallback, контент (с `sanitize`), lightbox для картинок.
- `renderError(message)` — сообщения об ошибках/отсутствии статьи.
- `renderLoading()` — спиннер в области контента.
- `setupShareButtons(article)` — обработчики для TG/FB/X/WA и кнопки копирования.

## Кеш и связи
- `getCacheOrFetch(limit=120)` — отдаёт прогретый `window.__newsCache` или загружает заново.
- `fetchRelatedAndLatest(baseArticle)` — подбирает «схожі» (по категории и пересечению тегов) и «останнi».

## Инициализация
- `loadArticle()` — оркестратор загрузки/рендера + SEO‑title.
- `initPage(root=document)` — вызывает `loadArticle`.
- `DOMContentLoaded` → `initPage()` — автоинициализация.

— Навигация —