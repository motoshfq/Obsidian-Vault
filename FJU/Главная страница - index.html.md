[[Структура проекта]]

#FJU
### 🗂 Структура main:

```html
<main>
  <section id="home" class="hero">...</section>
  <section class="info-section">...</section>
</main>
```

---

## 🥋 home.hero — главный блок

### 🎨 HTML:

```html
<section id="home" class="hero" itemscope itemtype="https://schema.org/SportsOrganization">
  <div class="hero-bg-elements">
    <div class="tatami-pattern"></div>
    <div class="floating-belt belt-white"></div>
    <div class="floating-belt belt-yellow"></div>
    <div class="floating-belt belt-orange"></div>
    <div class="floating-belt belt-green"></div>
    <div class="floating-belt belt-blue"></div>
    <div class="floating-belt belt-brown"></div>
    <div class="floating-belt belt-black"></div>
  </div>

  <div class="hero-container">
    <div class="hero-main-content">
      <div class="hero-badge">
        <svg>...</svg>
        <span>33 роки досвіду • Неофіційний веб-сайт</span>
      </div>

      <h1 class="hero-title">
        <span class="title-main">Федерація Дзюдо</span>
        <span class="title-ukraine">України</span>
        <span class="title-subtitle">Перемагаємо разом з 1991 року</span>
      </h1>

      <p class="hero-description">
        🥋 Розвиваємо дзюдо по всій Україні. Готуємо чемпіонів, організовуємо змагання...
      </p>

      <div class="hero-action-cards">
        <a href="about.html" class="action-card primary">...</a>
        <a href="team.html" class="action-card secondary">...</a>
        <a href="calendar.html" class="action-card accent">...</a>
      </div>
    </div>

    <div class="hero-stats-panel">
      <div class="stats-header">
        <h3>Досягнення ФДУ</h3>
        <div class="stats-indicator"></div>
      </div>

      <div class="stats-grid">
        <div class="stat-item" data-stat="athletes">
          <div class="stat-number" data-target="500">0</div>
          <div class="stat-label">Професійних спортсменів</div>
        </div>
        <div class="stat-item" data-stat="regions">
          <div class="stat-number" data-target="25">0</div>
          <div class="stat-label">Регіонів</div>
        </div>
        <div class="stat-item" data-stat="experience">
          <div class="stat-number" data-target="33">0</div>
          <div class="stat-label">Років досвіду</div>
        </div>
      </div>

      <div class="stats-footer">
        <p>Дані станом на 2025 рік</p>
      </div>
    </div>
  </div>

  <div class="scroll-indicator">
    <div class="scroll-text">Прокрутіть для більшої інформації</div>
    <div class="scroll-arrow"><svg>...</svg></div>
  </div>
</section>
```
![[FJU-home-main.png]]

🧠 **Особенности:**

- Много декоративных SVG: пояса (`belt-*`), иконки, стрелки.
    
- Карточки-ссылки — быстрый доступ к разделам.
    
- `data-target` в `stat-number` используется для анимации чисел.

---

## ℹ️ .info-section — блок про Федерацію

### 📄 HTML:!

```html
<section class="info-section">
  <div class="info-container">
    <div class="info-header">
      <div class="info-badge">...</div>
      <h2 class="info-title">Про Федерацію Дзюдо України</h2>
      <p class="info-subtitle">Дізнайтесь більше про історію...</p>
    </div>

    <div class="info-grid">
      <div class="info-card" data-card="history">
        <div class="info-card-icon"><svg>...</svg></div>
        <h3 class="info-card-title">Наша Історія</h3>
        <p class="info-card-description">З 1991 року ФДУ розвиває дзюдо...</p>
        <a href="about.html" class="info-card-link">Дізнатися більше <svg>...</svg></a>
      </div>

      <!-- Повторяется 4 раза с разным содержанием -->
      <div class="info-card" data-card="structure">...</div>
      <div class="info-card" data-card="achievements">...</div>
      <div class="info-card" data-card="events">...</div>
      <div class="info-card" data-card="regions">...</div>
    </div>
  </div>
</section>
```
![[FJU-home-about.png]]

🧠 **Особенности:**

- Карточки — стандартные, с SVG и описанием.
    
- Ссылки ведут на `about.html`, `calendar.html`, `team.html`.

---
## 📰 **Новостной виджет** 

Этот виджет отображает последние 3 новости на главной странице.

### 📌 Основные шаги:

```js
renderNewsWidget() {
  const newsData = this.calendarAPI.getNews().slice(0, 3);
  if (!newsData.length) return;

  const container = document.getElementById('newsPreview');
  newsData.forEach(news => {
    const card = document.createElement('div');
    card.className = 'news-card';

    // Создание и наполнение карточки
    card.innerHTML = `
      <h3 class="news-title">${news.title}</h3>
      <p class="news-snippet">${news.snippet}</p>
      <a class="news-link" href="news.html?id=${news.id}">Читати далі</a>
    `;

    container.appendChild(card);
  });
}
```

### 💡 Комментарии:

- **Источник данных** — метод `getNews()` из `CalendarAPI` (API для работы с SuperBase).
    
- **Формат карточек**:
    
    - Заголовок
        
    - Превью/сниппет текста
        
    - Ссылка на полную новость
    
- **HTML вставляется динамически** через `innerHTML`.
    
- Работает, если в разметке есть контейнер с `id="newsPreview"`.!
![[FJU-home-news.png]]
---

## 📅 **Календарный виджет** 

Календарный блок состоит из:

-  📆 **Предстоящие события**
    
-  🔴 **Текущие события** (если идут прямо сейчас)

### 📌 Основная логика (упрощённо):

```js
renderEvents(events) {
  events.forEach(event => {
    const card = document.createElement('div');
    card.className = 'event-card';
    // Заполнение карточки деталями события
    ...
    container.appendChild(card);
  });
}
```

### 🧠 Что показывает:

- Название события
    
- Дата
    
- Статус (`upcoming`, `ongoing`, `completed`)
    
- Город
    
- Весовые категории (парсятся отдельно)
    
- Кнопки: “Детальніше”, “Поділитися”

### 🔁 renderCurrentEventsSlider()

Отдельно создаётся **слайдер для текущих событий**, с переключателями и индикаторами:

```js
renderCurrentEventsSlider(events) {
  const slider = document.getElementById('currentEventsSlider');
  ...
  // Добавление карточек в слайдер
}
```

- **Автопереключение** событий
    
- **Навигация**: кнопки “←” и “→”
    
- **Поддержка динамического обновления** при смене даты
![[FJU-home-events.png]]
---
## 🎛️ Расположение в HTML

Эти виджеты рендерятся в заранее подготовленные блоки:

```html
<div id="newsPreview" class="news-section"></div>
<div id="upcomingEventsGrid" class="events-section"></div>
<div id="currentEventsSlider" class="slider-section"></div>
```
## 🧠 Скрипт: info.js

Код анимирует `info-section`, делает карточки интерактивными:

```js
class InfoSectionManager {
  init() {
    this.setupIntersectionObserver();   // Анимация при появлении
    this.setupCardInteractions();       // Поднятие карточек при hover
    this.setupBadgeInteraction();       // Масштаб бейджа
  }

  animateCardsIn() {
    this.cards.forEach((card, index) => {
      setTimeout(() => {
        card.classList.add('animate-in');
        card.style.opacity = '1';
        card.style.transform = 'translateY(0)';
      }, index * 200);
    });
  }

  onCardHover(card, isHover) {
    card.style.transform = isHover ? 'translateY(-15px)' : 'translateY(0)';
    ...
  }
}

document.addEventListener('DOMContentLoaded', () => {
  new InfoSectionManager();
});
```

📌 **Интерактив:**

- Карточки появляются поочерёдно (через `IntersectionObserver`).
    
- Иконки анимируются (вращение и масштаб).
    
- Бейдж масштабируется при наведении.
    

---

Вот полный **разбор файла `home.js`**, включая **все функции и методы класса `HomeEventsWidget`** с пояснениями, что делает каждая из них. Подходит для вставки в Obsidian как подробный технический обзор JS-логики главной страницы.

---

## 📁 home.js — логика событий и новостей

Основной класс — `HomeEventsWidget`, который управляет рендером **новостей**, **предстоящих событий**, **текущих мероприятий** и **интерактивных виджетов** на главной странице.

---

### 🧱 class HomeEventsWidget

```js
class HomeEventsWidget {
    constructor() {
        this.eventsContainer = document.getElementById('upcomingEventsGrid');
        this.sliderContainer = document.getElementById('currentEventsSlider');
        this.sliderNav = document.getElementById('sliderNavigation');
        this.sliderIndicators = document.getElementById('sliderIndicators');
        this.newsContainer = document.getElementById('newsPreview');
        this.currentSlideIndex = 0;

        this.init();
    }
```

### 🧪 `init()`

Главная точка входа.

```js
async init() {
    this.showLoading();
    this.calendarAPI = new CalendarAPI();
    await this.calendarAPI.loadData();

    const upcomingEvents = this.calendarAPI.getUpcomingEvents(3);
    const currentEvents = this.calendarAPI.getEvents().filter(...);
    const news = this.calendarAPI.getNews().slice(0, 3);

    this.renderEvents(upcomingEvents);
    this.renderCurrentEventsSlider(currentEvents);
    this.renderNewsWidget(news);
}
```

📌 **Что делает:**

- Загружает данные с API[^1].
    
- Отбирает:
    
    - ближайшие события (до 3),
        
    - текущие (`ongoing`) события,
        
    - последние 3 новости.
        
- Рендерит всё на страницу.

---

### ⏳ showLoading()

Показывает "скелетоны" вместо контента, пока грузится API.

```js
showLoading() {
    if (this.eventsContainer) {
        for (let i = 0; i < 3; i++) {
            const skeleton = document.createElement('div');
            skeleton.className = 'event-card-skeleton';
            this.eventsContainer.appendChild(skeleton);
        }
    }
}
```

---

### 📰 renderNewsWidget(news)

Отображает 3 новости в блоке `#newsPreview`.

```js
renderNewsWidget(news) {
    if (!this.newsContainer || !news.length) return;

    news.forEach(article => {
        const card = document.createElement('div');
        card.className = 'news-card';
        card.innerHTML = `
            <h3 class="news-title">${article.title}</h3>
            <p class="news-snippet">${article.snippet}</p>
            <a class="news-link" href="news.html?id=${article.id}">Читати далі</a>
        `;
        this.newsContainer.appendChild(card);
    });
}
```

---

### 📅 renderEvents(events)

Рендерит карточки **предстоящих событий**.

```js
renderEvents(events) {
    if (!this.eventsContainer || !events.length) return;
    this.eventsContainer.innerHTML = '';

    events.forEach(event => {
        const card = document.createElement('div');
        card.className = 'event-card';
        card.dataset.eventId = event.id;

        const date = new Date(event.start_date);
        const day = date.getDate();
        const month = date.toLocaleString('uk-UA', { month: 'long' });

        card.innerHTML = `
            <div class="event-date">...</div>
            <h3 class="event-title">${event.title}</h3>
            <p class="event-description">${event.description}</p>
            ...
        `;

        this.eventsContainer.appendChild(card);
    });
}
```

📌 **Особенности:**

- Использует `toLocaleString` для отображения месяца.
    
- Внутри вызывается `parseWeightCategories()` для добавления категорий.

---

### ⚖️ parseWeightCategories(event)

Анализирует строку категорий веса и возвращает массив.

```js
parseWeightCategories(event) {
    const parse = str => str?.split(',').map(s => s.trim()).filter(Boolean);
    const men = parse(event.details.weights_men);
    const women = parse(event.details.weights_women);

    return {
        menWeights: men,
        womenWeights: women,
        allWeightCategories: [...men, ...women]
    };
}
```

---

### 🎞️ renderCurrentEventsSlider(events)

Создаёт **слайдер текущих мероприятий**.

```js
renderCurrentEventsSlider(events) {
    if (!this.sliderContainer || !events.length) return;

    this.sliderContainer.innerHTML = '';
    this.sliderIndicators.innerHTML = '';
    this.sliderNav.innerHTML = '';

    events.forEach((event, index) => {
        const slide = document.createElement('div');
        slide.className = 'slider-slide';
        if (index === 0) slide.classList.add('active');
        slide.innerHTML = `
            <h3>${event.title}</h3>
            <p>${event.description}</p>
            <a href="calendar.html?id=${event.id}">Детальніше</a>
        `;
        this.sliderContainer.appendChild(slide);

        const indicator = document.createElement('span');
        indicator.className = 'slider-indicator';
        if (index === 0) indicator.classList.add('active');
        this.sliderIndicators.appendChild(indicator);
    });

    // Навигационные стрелки
    const prevBtn = document.createElement('button');
    prevBtn.className = 'slider-prev';
    prevBtn.innerText = '←';
    prevBtn.addEventListener('click', () => this.changeSlide(-1));

    const nextBtn = document.createElement('button');
    nextBtn.className = 'slider-next';
    nextBtn.innerText = '→';
    nextBtn.addEventListener('click', () => this.changeSlide(1));

    this.sliderNav.appendChild(prevBtn);
    this.sliderNav.appendChild(nextBtn);
}
```

📌 **Функции слайдера:**

- Отображает несколько слайдов (один активный).
    
- Индикаторы (`dots`) переключаются.
    
- Навигация кнопками.

---

### 🔁 changeSlide(direction)

Меняет активный слайд в слайдере.

```js
changeSlide(direction) {
    const slides = document.querySelectorAll('.slider-slide');
    const indicators = document.querySelectorAll('.slider-indicator');
    slides[this.currentSlideIndex].classList.remove('active');
    indicators[this.currentSlideIndex].classList.remove('active');

    this.currentSlideIndex = (this.currentSlideIndex + direction + slides.length) % slides.length;

    slides[this.currentSlideIndex].classList.add('active');
    indicators[this.currentSlideIndex].classList.add('active');
}
```

---
## 📌 Заключение

| Метод                                  | Назначение                                        |
| -------------------------------------- | ------------------------------------------------- |
| [[#🧪 `init()`]]                       | Главная инициализация и вызов всех других методов |
| [[#⏳ `showLoading()`]]                 | Отображение скелетонов                            |
| [[#📰 `renderNewsWidget(news)`]]       | Генерация новостных карточек                      |
| [[#📅 `renderEvents(events)`]]         | Отрисовка ближайших мероприятий                   |
| [[#⚖️ `parseWeightCategories(event)`]] | Парсинг строк весовых категорий                   |
| [[#🔁 `renderCurrentEventsSlider()`]]  | Слайдер для текущих мероприятий                   |
| [[#🔁 `changeSlide(direction)`]]       | Переключение между слайдами                       |


[^1]: **CalendarAPI** изначально задумывался как простое API для загрузки событий из таблицы `events` в Supabase. Но со временем появились новые функции — **Event Page**, **News Widget** и другие. Каждой из них требовался доступ к тем же данным, и писать отдельные функции для каждой было неудобно и неэффективно. Чтобы избежать дублирования и потери оптимизации, было решено объединить все обращения к Supabase — от Calendar, Event Page, Event Widget и News Widget — в одно общее API: **CalendarAPI**.
