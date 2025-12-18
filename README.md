Wiki Automation Project
Набор UI-автотестов для русской Википедии (web) и Android-приложения Wikipedia на связке Selenium + TestNG + Appium.

🚀 Быстрый старт
bash
# Клонировать репозиторий
git clone https://github.com/your-username/wiki-automation.git
cd wiki-automation

# Запустить web-тесты
mvn clean test -Pweb

# Запустить mobile-тесты
mvn clean test -Pmobile
📋 Стек технологий
Компонент	Технология
Язык	Java 11
Сборка	Maven
Тестовый фреймворк	TestNG
Web-тестирование	Selenium WebDriver, WebDriverManager
Mobile-тестирование	Appium Java Client, Appium Server (uiautomator2)
📁 Структура проекта
text
├── pom.xml                    # зависимости и профили Maven
├── src/
│   └── test/
│       ├── java/com/automation/
│       │   ├── config/
│       │   │   └── TestConfig.java    # конфигурация (web + mobile)
│       │   ├── web/                   # страницы и тесты веб-Википедии
│       │   │   ├── pages/             # Page Object Model
│       │   │   └── tests/             # Web тесты
│       │   └── mobile/                # страницы и тесты Android-приложения
│       │       ├── pages/             # Page Object Model
│       │       └── tests/             # Mobile тесты
│       └── resources/
│           ├── config.properties      # настройки окружения
│           ├── testng-web.xml         # web-тест suite
│           └── testng-mobile.xml      # mobile-тест suite
└── README.md                   # этот файл
⚙️ Настройка окружения
1. Установка необходимого ПО
Для web-тестов:

JDK 11+

Maven 3.8+

Браузер Chrome или Firefox

Для mobile-тестов (дополнительно):

Node.js + Appium:

bash
npm install -g appium
appium driver install uiautomator2
Android Studio с установленным Android SDK

Эмулятор Android или физическое устройство

2. Настройка конфигурации
Отредактируйте файл src/test/resources/config.properties:

properties
# Web конфигурация
web.base.url=https://ru.wikipedia.org
web.browser=chrome
web.timeout.seconds=10

# Mobile конфигурация
mobile.platform.name=Android
mobile.platform.version=16
mobile.device.name=emulator-5554
mobile.automation.name=UiAutomator2
mobile.appium.server.url=http://127.0.0.1:4723
mobile.app.package=org.wikipedia
mobile.app.activity=org.wikipedia.main.MainActivity
▶️ Запуск тестов
Web-тесты
bash
mvn clean test -Pweb
Mobile-тесты
Запустите Appium сервер:

bash
appium
Запустите Android эмулятор или подключите устройство

Выполните тесты:

bash
mvn clean test -Pmobile
Запуск всех тестов
bash
mvn clean test -Pall
🧪 Тестовые сценарии
🌐 Web-сценарии
✅ Проверка отображения главной страницы

✅ Поиск статьи и проверка заголовка

✅ Переход по ссылке «Заглавная страница»

✅ Переход на страницу логина и проверка заголовка

📱 Mobile-сценарии
✅ Запуск приложения и проверка главного экрана

✅ Поиск статьи по ключевому слову и открытие первой статьи

✅ Проверка заголовка статьи

✅ Скролл и работа с оглавлением

✅ Поиск несуществующей статьи и проверка реакции приложения

🔧 Устранение неполадок
Проблемы с Appium
bash
# Проверка статуса сервера
curl http://127.0.0.1:4723/status

# Переустановка драйвера
appium driver uninstall uiautomator2
appium driver install uiautomator2
Проблемы с Android
bash
# Проверка подключенных устройств
adb devices

# Перезапуск ADB сервера
adb kill-server
adb start-server
Проблемы с Maven
bash
# Очистка кэша и обновление зависимостей
mvn clean install -U

# Пропуск тестов при сборке
mvn clean compile -DskipTests
