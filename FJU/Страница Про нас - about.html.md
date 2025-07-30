Конечно! Ниже — структурированная заметка в формате Markdown (`.md`), подходящая для использования в **Obsidian**. В ней описана **структура сайта** из файла `about.html`, **без учёта** шапки (header), подвала (footer) и SEO-метатегов. Основной акцент — на контентной части: навигация, разделы, структура данных, изображения, таймлайн и т.д.

---
## 📍 Общая структура страницы
	 
Страница `about.html` посвящена **описанию Федерації Дзюдо України (ФДУ)** и содержит следующие основные блоки:
- Цели ФДУ
- История ФДУ (таймлайн)
- Руководство и президенты
- Текущее руководство (президиум)
- Комиссии
- Партнеры (спонсоры)

---
## 🏁 1. Заголовок страницы (Page Header)

```html
<section class="page-header">
  <h1>Про Федерацію Дзюдо України</h1>
  <p class="page-subtitle">Офіційна інформація про ФДУ: історія створення з 1991 року, керівництво та досягнення української збірної з дзюдо</p>
</section>
```

- Основной заголовок: **"Про Федерацію Дзюдо України"**.
- Подзаголовок кратко описывает содержание страницы.
- Используется микроразметка `schema.org/SportsOrganization`.

---

## 🎯 2. Цели ФДУ

Раздел представлен в виде списка с нумерацией:

```html
<div class="goals-list">
  <div class="goal-item">
    <div class="goal-number">1</div>
    <p>Розвиток дзюдо в Україні, підвищення його ролі у всебічному і гармонійному розвитку особистості...</p>
  </div>
  <div class="goal-item">
    <div class="goal-number">2</div>
    <p>Поліпшення системи підготовки висококваліфікованих спортсменів, тренерів, суддів...</p>
  </div>
  <div class="goal-item">
    <div class="goal-number">3</div>
    <p>Розвиток і зміцнення зв'язків з міжнародними та іншими федераціями...</p>
  </div>
</div>
```

**Три основные цели:**
1. Развитие дзюдо и здорового образа жизни.
2. Подготовка спортсменов и тренеров для международных соревнований.
3. Международное сотрудничество.

---

## 📜 3. История ФДУ (таймлайн)

Раздел организован как **вертикальная хронология** (`timeline-item`), с чередованием текста и изображений.

### Ключевые события:

| Год | Событие |
|-----|-------|
| **21 січня 1991** | Основание ФДУ на конференции в Києві |
| **1974** | Сергій Новіков — бронза чемпіонату Європи (63 кг) |
| **1982** | Перший чемпіонат України з дзюдо |
| **1999** | Перший міжнародний турнір «Кубок України» |
| **2005** | Три медалі на ЧС у Каїрі: Віталій Бубон (срібло), Геннадій Білодід, Роман Гонтюк (бронза) |
| **2009** | Георгій Зантарая — чемпіон світу (90 кг) |
| **2011** | Чемпіонат світу серед кадетів у Києві |
| **2019** | Дарія Білодід та Георгій Зантарая — золото Європейських ігор |
| **2020–2021** | Пандемія, перенос ОІ-2020 в Токіо |

### Особенности:
- Используются блоки: `.timeline-year`, `.timeline-content`, `.history-image`.
- Изображения снабжены подписями (`history-image-caption`).
- Некоторые изображения имеют микроразметку `schema.org/ImageObject`.

---

## 👑 4. Керівництво ФДУ

### 5.1. Історія президентів

Список президентів з роками правління:

```html
<div class="president-item"><span class="president-years">1991-1993</span><span class="president-name">Віктор Клименко</span></div>
<div class="president-item"><span class="president-years">1993-1997</span><span class="president-name">Володимир Сівкович</span></div>
<div class="president-item"><span class="president-years">2013-2017</span><span class="president-name">Нуруліслам Аркаллаєв</span></div>
<div class="president-item"><span class="president-years">2017-2020</span><span class="president-name">Роман Насіров</span></div>
<div class="president-item current"><span class="president-years">З 2020</span><span class="president-name">Михайло Кошляк</span></div>
```

### 5.2. Поточне керівництво (президія)

Представлено в виде сетки карточек (`leader-card`):

| Посада | Ім'я | Місто |
|--------|------|-------|
| Президент | Михайло Кошляк | Київ |
| Перший віцепрезидент | Василь Волошин | Кременчук |
| Віцепрезиденти | Сергій Кolesніченко, Олександр Нагібін, Михайло Руденко | Суми, Київ, Київ |
| Спортивний директор | Віталій Дуброва | Київ |
| Виконавчий секретар | Наталія Редкіна | Київ |
| Радник президента | Григорій Король | Дніпро |
| Головний тренер | Віталій Дуброва | Київ |
| Відповідальна за зв’язки | Інна Скородідова | Київ |

> **Примечание**: В разделе "Поточне керівництво" используется микроразметка `schema.org/Person` и `schema.org/PostalAddress`.

---

## 🏛️ 5. Комісії ФДУ

Сетка из карточек комиссий (`commissions-grid`). Каждая комиссия включает:

- Название
- Руководителя (иногда с пометкой должности в ФДУ)
- Членов комиссии (в виде списка)
- Иногда — примечания (например, "член з правом дорадчого голосу")

### Список комісій:

1. **Суддівська комісія**
   - Голова: Алексєєв Анатолій Федотович
   - Члени: Дементьєв, Грицуняк, Германюк и др.

2. **ДАН комісія**
   - Голова: Алексєєв Анатолій Федотович
   - Заступник: Дуброва Віталій Вікторович

3. **Комісія атлетів**
   - Голова: Артем Лесюк
   - Члени: Дарія Білодід, Богдан Ядов, Єлизавета Литвиненко, Яків Хаммо

4. **Етико-дисциплінарна комісія**
   - Голова: Михайло Руденко (віцепрезидент)

5. **Комісія з проведення турнірів**
   - Голова: Олександр Кolesніченко (віцепрезидент)

6. **Комісія з міжнародних зв'язків**
   - Голова: Олександр Нагібін (віцепрезидент)

7. **Комісія з розвитку спорту ветеранів та інвалідів**
   - Голова: Анатолій Прокопець
   - Члени: Олександр Косінов и др.

> **Примечание**: Упоминается ссылка на документы: `<div class="documents-note">ДОКУМЕНТИ</div>`.

---

## 🤝 6. Партнери (спонсори)

Раздел "Наші партнери" содержит логотипы спонсоров:

```html
<div class="sponsors-grid">
  <div class="sponsor-item"><img src="assets/TAS_logo.png" alt="TAS"></div>
</div>
```

- На данный момент указан только один спонсор: **TAS**.
- Возможна динамическая загрузка других логотипов.

---
Конечно! Ниже — **подробная, структурированная заметка для Obsidian**, посвящённая **только CSS-файлам** сайта `about.html` (Федерація Дзюдо України).

Заметка включает:
- Общую архитектуру стилей,
- Назначение каждого CSS-файла,
- Краткий разбор ключевых стилей,
- Визуальную иерархию,
- Рекомендации и наблюдения.

---
# 🎨 Дизайн

> Подробное описание каждого CSS-файла по структуре страницы `about.html`.  
> Только стили. Без HTML, JS, SEO.

---
## 1. `header.css` — Заголовок страницы

**Отвечает за**: визуальное оформление верхней части страницы — фон, заголовок, подзаголовок, анимации.

### 🔧 Основные элементы:
- `.page-header` — контейнер с градиентом и анимированным фоном.
- `.page-title` — главный заголовок.
- `.page-subtitle` — поясняющий текст.

### 💡 Ключевые стили:
```css
.page-header {
  padding: 6rem 0 4rem;
  background: linear-gradient(135deg, var(--primary-color), var(--primary-light));
  color: var(--text-white);
  position: relative;
  overflow: hidden;
}

.page-header::before {
  content: '';
  position: absolute;
  background-image: url("data:image/svg+xml,...");
  animation: float 20s ease-in-out infinite;
}

@keyframes float {
  0% { transform: translateY(0) rotate(0deg); }
  50% { transform: translateY(-10px) rotate(180deg); }
  100% { transform: translateY(0) rotate(360deg); }
}

.page-header::after {
  content: '';
  position: absolute;
  bottom: 0;
  height: 60px;
  background: linear-gradient(to right, transparent, rgba(255,255,255,0.1), transparent);
  transform: skewY(-1deg);
}

.page-title {
  font-size: clamp(2rem, 5vw, 3.5rem);
  font-weight: 800;
  color: var(--text-white);
  text-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
}

.page-title::after {
  content: '';
  position: absolute;
  bottom: -0.5rem;
  left: 50%;
  transform: translateX(-50%);
  width: 3rem;
  height: 3px;
  background: var(--text-white);
  border-radius: 2px;
}
```

### 📱 Адаптивность:
```css
@media (max-width: 768px) {
  .page-header { padding: 4rem 0 3rem; }
  .page-title::after { width: 2.5rem; height: 2px; }
  .page-subtitle { font-size: 1.1rem; }
}
```

---

## 2. `presidium.css` — Президія (керівництво)

**Отвечает за**: карточки членов президії — их расположение, стиль, hover-эффекты, выделение президента.

### 🔧 Основные элементы:
- `.presidium-section` — секция с фоном и сеткой.
- `.presidium-member` — карточка одного члена.
- `.member-number` — номер в списке (кружок).
- `.member-name`, `.member-position` — текстовые поля.

### 💡 Ключевые стили:
```css
.presidium-section {
  padding: 5rem 0;
  background: var(--bg-light);
  position: relative;
}

.presidium-section::before {
  content: '';
  position: absolute;
  background: url('data:image/svg+xml,...') repeat;
  opacity: 0.4;
}

.presidium-list {
  display: grid;
  gap: 1.8rem;
  max-width: 900px;
  margin: 0 auto;
}

.presidium-member {
  background: var(--bg-white);
  border-radius: 16px;
  padding: 2rem;
  border-left: 5px solid var(--primary-color);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.06);
  display: flex;
  align-items: center;
  gap: 1.5rem;
  transition: all 0.4s ease;
}

.presidium-member:hover {
  transform: translateX(12px) translateY(-2px);
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.15);
}

.presidium-member:first-child {
  background: linear-gradient(135deg, var(--primary-color), var(--primary-light));
  color: var(--text-white);
  transform: scale(1.03);
}

.member-number {
  width: 2.5rem;
  height: 2.5rem;
  background: linear-gradient(135deg, var(--primary-color), var(--primary-light));
  color: var(--text-white);
  border-radius: 50%;
  font-weight: 800;
  font-size: 1rem;
}
```

### 📱 Адаптивность:
```css
@media (max-width: 768px) {
  .presidium-member {
    flex-direction: column;
    text-align: center;
  }
  .member-number {
    margin-bottom: 0.5rem;
  }
}
```

---

## 3. `commissions.css` — Комісії

**Отвечает за**: сетку и карточки комісій — их оформление, заголовки, списки членов, hover-эффекты.

### 🔧 Основные элементы:
- `.commissions-section` — общая секция.
- `.commission-card` — отдельная карточка комісії.
- `.commission-title` — название комісії.
- `.role-title` — должность (например, "Голова").
- `.role-members` — список членов.

### 💡 Ключевые стили:
```css
.commissions-section {
  padding: 5rem 0;
  background: var(--bg-light);
  position: relative;
}

.commissions-section::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0; bottom: 0;
  background: url('data:image/svg+xml,...') repeat;
  opacity: 0.4;
}

.commissions-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

.commission-card {
  background: var(--bg-white);
  border-radius: 16px;
  padding: 2rem;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  transition: all 0.3s ease;
  border-top: 4px solid var(--primary-color);
}

.commission-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.12);
}

.commission-title {
  font-size: 1.4rem;
  font-weight: 700;
  margin-bottom: 1.5rem;
  color: var(--text-dark);
  border-bottom: 2px solid var(--primary-color);
  padding-bottom: 0.5rem;
}

.role-title {
  font-weight: 600;
  color: var(--text-dark);
  font-size: 1rem;
  margin: 1rem 0 0.5rem;
}

.role-members li {
  padding-left: 1rem;
  position: relative;
  transition: all 0.3s ease;
}

.role-members li:hover {
  padding-left: 1.2rem;
  color: var(--primary-color);
}

.member-note {
  font-size: 0.8rem;
  color: var(--text-light);
  font-style: italic;
}

.documents-note {
  padding: 0.8rem;
  font-size: 0.85rem;
  text-align: center;
  margin-top: 1.5rem;
  color: var(--text-light);
  border-top: 1px dashed var(--text-light);
}
```

### 📱 Адаптивность:
```css
@media (max-width: 768px) {
  .commissions-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
    padding: 0 1rem;
  }
  .commission-card { padding: 1.5rem; }
  .role-title { font-size: 0.85rem; }
  .role-members li { font-size: 0.95rem; }
}
```

---

## 4. `federation-info.css` — Цели и партнёры

**Отвечает за**: блоки с целями ФДУ и логотипы спонсоров.

### 🔧 Основные элементы:
- `.goals-list` — список целей.
- `.goal-item` — один пункт цели.
- `.goal-number` — цифра в кружке.
- `.sponsors-grid` — сетка логотипов.
- `.sponsor-item` — одна карточка спонсора.
- `.sponsor-logo` — сам логотип.

### 💡 Ключевые стили:
```css
.goals-list {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  max-width: 800px;
  margin: 0 auto 3rem;
}

.goal-item {
  display: flex;
  gap: 1rem;
  align-items: flex-start;
}

.goal-number {
  flex-shrink: 0;
  width: 2.5rem;
  height: 2.5rem;
  background: linear-gradient(135deg, var(--primary-color), var(--primary-light));
  color: var(--text-white);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 800;
  font-size: 1.1rem;
}

.sponsors-grid {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 2rem;
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem 0;
}

.sponsor-item {
  display: flex;
  align-items: center;
  justify-content: center;
  width: calc(16.666% - 2rem);
  height: 120px;
  background: white;
  border-radius: 12px;
  padding: 1.5rem;
  transition: all 0.3s ease;
  border: 1px solid rgba(26, 63, 103, 0.1);
  box-shadow: 0 4px 15px rgba(26, 63, 103, 0.05);
}

.sponsor-item:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 25px rgba(26, 63, 103, 0.1);
  border-color: rgba(26, 63, 103, 0.2);
}

.sponsor-logo {
  max-width: 90%;
  max-height: 100%;
  object-fit: contain;
  filter: opacity(0.8);
  transition: all 0.3s ease;
}

.sponsor-item:hover .sponsor-logo {
  opacity: 1;
  transform: scale(1.05);
}
```

---

## 5. `history.css` — История ФДУ

**Отвечает за**: хронологию событий — таймлайн, изображения, подписи.

### 🔧 Основные элементы:
- `.history-section` — общая секция.
- `.timeline` — центральная линия.
- `.timeline-item` — одно событие.
- `.timeline-year` — год события.
- `.timeline-content` — текст события.
- `.history-image` — изображение к событию.
- `.history-image-caption` — подпись под изображением.

### 💡 Ключевые стили:
```css
.history-section {
  padding: 5rem 0;
  background: white;
}

.history-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.timeline {
  position: relative;
  max-width: 800px;
  margin: 0 auto;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 50%;
  top: 0;
  bottom: 0;
  width: 2px;
  background: linear-gradient(to bottom, transparent, var(--primary-color) 20%, var(--primary-light) 80%, transparent);
  transform: translateX(-50%);
}

.timeline-item {
  position: relative;
  display: flex;
  margin-bottom: 4rem;
}

.timeline-item:nth-child(even) {
  flex-direction: row-reverse;
}

.timeline-year {
  flex: 0 0 140px;
  font-size: 1.1rem;
  font-weight: 700;
  color: var(--primary-color);
  text-align: center;
  padding: 0.5rem 1rem;
  background: var(--bg-light);
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
  align-self: flex-start;
}

.timeline-content {
  flex: 1;
  background: var(--bg-white);
  padding: 2rem;
  border-radius: 16px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.06);
  border: 1px solid rgba(var(--primary-rgb), 0.1);
  transition: all 0.3s ease;
}

.timeline-content:hover {
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.12);
  transform: translateY(-4px);
}

.history-image {
  max-width: 300px;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
}

.history-image img {
  width: 100%;
  height: auto;
  display: block;
  transition: transform 0.4s ease;
}

.history-image:hover img {
  transform: scale(1.05);
}

.history-image-caption {
  font-size: 0.9rem;
  color: var(--text-light);
  text-align: center;
  margin-top: 0.5rem;
  font-style: italic;
}
```

### 📱 Адаптивность:
```css
@media (max-width: 768px) {
  .timeline::before { left: 30px; transform: translateX(0); }
  .timeline-item { flex-direction: row !important; }
  .timeline-year { flex: 0 0 120px; }
  .history-image { max-width: 200px; }
}
```

---

## 6. `leadership.css` — Список президентов

**Отвечает за**: историю руководства — список президентов с годами.

### 🔧 Основные элементы:
- `.leadership-grid` — контейнер для списка.
- `.president-item` — один президент.
- `.president-years` — период правления.
- `.president-name` — имя.
- `.current` — текущий президент.

### 💡 Ключевые стили:
```css
.leadership-grid {
  display: flex;
  flex-direction: column;
  gap: 0.8rem;
  max-width: 400px;
  margin: 0 auto 3rem;
  padding: 2rem;
  background: var(--bg-white);
  border-radius: 16px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.06);
}

.president-item {
  display: flex;
  justify-content: space-between;
  padding: 0.8rem 1rem;
  border-left: 3px solid var(--primary-color);
  transition: all 0.3s ease;
}

.president-item:hover {
  background: var(--bg-light);
  border-left-color: var(--primary-light);
}

.president-years {
  font-weight: 600;
  color: var(--primary-color);
  min-width: 100px;
}

.president-name {
  font-weight: 500;
  color: var(--text-dark);
  flex: 1;
}

.current {
  background: var(--primary-light);
  color: var(--text-white);
  font-weight: 700;
}

.current .president-name {
  color: var(--text-white);
}

.current .president-years {
  color: var(--primary-color);
}
```
## 📎 Связанные заметки 
- [[Структура проекта]]

