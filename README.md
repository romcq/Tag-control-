https://romcq.github.io/Tag-control-/

# 🍞 Контроль технических параметров (тегов) на производстве хлеба

## 🔄 Краткий процесс производства хлеба
![Хлеб - bpmn drawio](https://github.com/user-attachments/assets/660120a6-ee4e-4222-be0e-e6e60204fb17)

## 📊 Какие теги контролируются на каждом этапе
![Untitled diagram-2025-02-16-153551](https://github.com/user-attachments/assets/ded94ae3-c3eb-4e44-babc-c595ad6de7a2)

## 🏗 Архитектура
![Архитектура drawio](https://github.com/user-attachments/assets/9f2bdcbf-2c6e-4531-b794-4899a439ed56)

---

## 📌 Основные компоненты

### 🛰 1. Сервис сбора тегов из трафика (`traffic_collector`) (НЕ РЕАЛИЗУЕМ, ПРОСТО ДЛЯ СХЕМЫ)
- 📡 Извлекает данные из сетевого трафика (OPC UA, MQTT, HTTP).
- 🔄 Передает актуальные значения тегов в базу `tags_bd`.

### 🗄 2. База значений тегов (`tags_bd`)
- 🏭 Хранит актуальные значения технологических параметров.
- ⏳ Записывает данные в реальном времени.
- 📌 Включает временные метки, идентификатор оборудования и текущие значения параметров.

### 📜 3. База правил (`rules_bd`)
- 📋 Содержит допустимые диапазоны значений для каждого тега.
- 🔧 Обновляется через веб-приложение или автоматически.
- ✏ Позволяет добавлять, изменять и удалять правила.

### ⚙ 4. Сервис проверки соответствия тегов правилам (`tags_filter`)
- 📥 Запрашивает значения из `tags_bd`.
- 🔍 Сравнивает полученные значения с `rules_bd`.
- 🛑 Определяет статус тега:
  - ✅ **В норме** → Белый фон.
  - ⚠ **Предупреждение** → Желтый фон.
  - ❌ **Критическое нарушение** → Красный фон.
- 📤 Отправляет результаты в `Веб-приложение`.

### 🖥 5. Веб-приложение (`frontend`)
- 📊 Визуализирует статус тегов.
- 🎛 Позволяет оператору:
  - 📡 Просматривать текущие значения параметров.
  - 📝 Изменять правила в `rules_bd`.
  - 🚨 Получать уведомления о нарушениях.
- 🔄 Работает в режиме реального времени.

---
