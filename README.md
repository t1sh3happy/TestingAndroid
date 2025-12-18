# Testing Project
## 📋 Описание проекта
Проект содержит автоматизированные тесты для:

Веб-сайта ru.wikipedia.org (4 теста)
Мобильного приложения Wikipedia (5 тестов)

## 🛠 Технологии
Java 11+
Selenium WebDriver
Appium
TestNG
Maven
WebDriverManager
Appium Java Client

## 📋 Требования
Основные:
Установить Java 11+
Установить Maven 3.8+
Установить Git
Для веб-тестов:
Установить Chrome браузер
Для мобильных тестов:
Установить Appium:             
                npm install -g appium
                appium driver install uiautomator2
                Установить Android Studio
                
                Создать эмулятор Android (рекомендуется API 30+)
                
                Установить приложение Wikipedia на эмулятор

## 🚀 Запуск тестов
Все тесты
```
mvn clean test
```
### 1. Веб-тесты (сайт ru.wikipedia.org)
```
mvn clean test -Pweb
```


### 2. Мобильные тесты (приложение Wikipedia)
Приложение должно быть установлено на устройство/эмулятор

Последовательность запуска:

Запуск Android эмулятора

```
emulator -avd Pixel_5
```


Проверка подключения устройства

```
adb devices
```
Запуск Appium сервера

```
appium -p 4723
```


Запуск мобильных тестов

```
mvn clean test -Pmobile
```
📁 Структура проекта
text
src/test/java/com/automation/
├── config/           # Конфигурация тестов
├── web/              # Веб-тесты и Page Objects
└── mobile/           # Мобильные тесты и Page Objects
🔧 Настройка
Перед запуском отредактируйте файл src/test/resources/config.properties:

properties
# Для веб-тестов
web.base.url=https://ru.wikipedia.org
web.browser=chrome

# Для мобильных тестов
mobile.device.name=emulator-5554
mobile.platform.version=16
🧪 Тестовые сценарии
Веб-тесты:
✅ Проверка главной страницы

✅ Поиск статьи

✅ Навигация по сайту

✅ Страница входа

Мобильные тесты:
✅ Запуск приложения

✅ Поиск статьи

✅ Открытие статьи

✅ Навигация по контенту

✅ Поиск несуществующей статьи

🔍 Устранение проблем
Проблемы с Appium:
bash
# Проверка установки
appium --version

# Переустановка драйвера
appium driver uninstall uiautomator2
appium driver install uiautomator2
Проблемы с эмулятором:
bash
# Список доступных эмуляторов
emulator -list-avds

# Перезагрузка ADB
adb kill-server
adb start-server
Проблемы с зависимостями:
bash
# Очистка и обновление
mvn clean install -U
