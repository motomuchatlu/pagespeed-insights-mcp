# PageSpeed Insights MCP Server

[![npm version](https://badge.fury.io/js/pagespeed-insights-mcp.svg)](https://www.npmjs.com/package/pagespeed-insights-mcp)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

MCP сервер для Google PageSpeed Insights API, що дозволяє аналізувати продуктивність веб-сторінок безпосередньо через Claude.

## ✨ Особливості

- 🚀 **Аналіз продуктивності** веб-сторінок за допомогою Google PageSpeed Insights
- 📱 **Підтримка всіх платформ**: мобільних та десктопних пристроїв
- 🔍 **Детальні звіти Lighthouse** з усіма метриками
- 📊 **Спрощені звіти** з основними показниками продуктивності
- 🌍 **Локалізація** - підтримка різних мов
- ⚡ **Швидке встановлення** - одна команда для налаштування
- 🐳 **Docker підтримка** для контейнеризованого розгортання

## 🚀 Швидке встановлення

### Варіант 1: Автоматичне встановлення (рекомендовано)

```bash
curl -sSL https://raw.githubusercontent.com/ruslanlap/pagespeed-insights-mcp/main/install.sh | bash
```

### Варіант 2: Через npm

```bash
# Глобальне встановлення
npm install -g pagespeed-insights-mcp

# Або використання без встановлення
npx pagespeed-insights-mcp
```

### Варіант 3: Docker

```bash
docker build -t pagespeed-insights-mcp .
docker run -e GOOGLE_API_KEY=your-key pagespeed-insights-mcp
```

## 🔑 Отримання Google API ключа

1. Перейдіть до [Google Cloud Console](https://console.cloud.google.com/)
2. Створіть новий проект або оберіть існуючий
3. Увімкніть PageSpeed Insights API:
   - Перейдіть до "APIs & Services" → "Library"
   - Знайдіть "PageSpeed Insights API" та увімкніть його
4. Створіть API ключ:
   - Перейдіть до "APIs & Services" → "Credentials"
   - Натисніть "Create Credentials" → "API Key"
   - Скопіюйте створений ключ

## ⚙️ Налаштування Claude Desktop

### Автоматичне налаштування
Якщо ви використали install.sh скрипт, конфігурація була створена автоматично.

### Ручне налаштування

Додайте конфігурацію до файлу Claude Desktop:

**macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`  
**Windows:** `%APPDATA%\Claude\claude_desktop_config.json`  
**Linux:** `~/.config/claude/claude_desktop_config.json`

#### Для npm установки:
```json
{
  "mcpServers": {
    "pagespeed-insights": {
      "command": "npx",
      "args": ["pagespeed-insights-mcp"],
      "env": {
        "GOOGLE_API_KEY": "your-google-api-key-here"
      }
    }
  }
}
```

#### Для глобальної установки:
```json
{
  "mcpServers": {
    "pagespeed-insights": {
      "command": "pagespeed-insights-mcp",
      "env": {
        "GOOGLE_API_KEY": "your-google-api-key-here"
      }
    }
  }
}
```

#### Для Docker:
```json
{
  "mcpServers": {
    "pagespeed-insights": {
      "command": "docker",
      "args": [
        "run", "--rm", "-i",
        "--env", "GOOGLE_API_KEY=your-google-api-key-here",
        "pagespeed-insights-mcp"
      ]
    }
  }
}
```

**Перезапустіть Claude Desktop** після налаштування!

## 💻 Використання

Після налаштування просто напишіть Claude будь-що з цих команд:

### 🔍 Повний аналіз сторінки
```
Проаналізуй продуктивність сайту https://example.com
```

### 📱 Аналіз для мобільних пристроїв
```
Проаналізуй https://example.com для мобільних пристроїв з усіма категоріями
```

### ⚡ Швидкий огляд продуктивності
```
Отримай короткий звіт про продуктивність https://example.com
```

### 🖥️ Аналіз для десктопу
```
Analyze https://example.com performance for desktop devices
```

### 🌐 Мультикатегорійний аналіз
```
Проведи повний аудит https://example.com включаючи SEO, доступність та найкращі практики
```

## Доступні інструменти

### `analyze_page_speed`

Повний аналіз сторінки з усіма метриками Lighthouse.

**Параметри:**
- `url` (обов'язковий): URL сторінки для аналізу
- `strategy`: "mobile" або "desktop" (за замовчуванням: "mobile")
- `category`: масив категорій ["performance", "accessibility", "best-practices", "seo", "pwa"]
- `locale`: локаль для результатів (за замовчуванням: "en")

### `get_performance_summary`

Спрощений звіт з основними метриками продуктивності.

**Параметри:**
- `url` (обов'язковий): URL сторінки для аналізу
- `strategy`: "mobile" або "desktop" (за замовчуванням: "mobile")

## Розробка

```bash
# Режим розробки
npm run dev

# Збірка проекту
npm run build

# Запуск збудованого сервера
npm start
```

## Усунення проблем

### "Google API key not provided"
Переконайтеся, що змінна середовища `GOOGLE_API_KEY` встановлена в конфігурації Claude Desktop.

### "PageSpeed Insights API error: 403"
Перевірте, чи увімкнений PageSpeed Insights API у вашому Google Cloud проекті.

### "Invalid URL"
Переконайтеся, що URL містить протокол (http:// або https://).

## Ліцензія

MIT

## Підтримка

Для звіту про проблеми або запитів нових функцій, будь ласка, створіть issue в репозиторії.