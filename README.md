Wiki Automation Project — набор UI‑автотестов для русской Википедии (web) и Android‑приложения Wikipedia на связке Selenium + TestNG + Appium.

Стек и структура
Язык: Java 11

Сборка: Maven

Тестовый фреймворк: TestNG

Web: Selenium WebDriver, WebDriverManager

Mobile: Appium Java Client, Appium Server (uiautomator2)

Основная структура:

pom.xml — зависимости и профили web / mobile

src/test/java/com/automation/config/TestConfig.java — конфиг (web + mobile)

src/test/java/com/automation/web/... — страницы и тесты веб‑Википедии

src/test/java/com/automation/mobile/... — страницы и тесты Android‑приложения

src/test/resources/config.properties — настройки окружения

src/test/resources/testng-web.xml — web‑suite

src/test/resources/testng-mobile.xml — mobile‑suite​

Подготовка окружения
1. Установки
JDK 11+

Maven 3.8+

Node.js + Appium 3:

bash
npm install -g appium
appium driver install uiautomator2
Android SDK (через Android Studio или отдельно)

2. Переменные среды (Windows)
В переменные пользователя:

ANDROID_HOME = C:\Users\<USER>\AppData\Local\Android\Sdk

ANDROID_SDK_ROOT = тот же путь

В Path добавить:

...\Android\Sdk\platform-tools

Проверка:

bash
adb version
3. Эмулятор / устройство
Создать AVD (например, API 16 или 30) и запустить его.

Проверить:

bash
adb devices
# должен быть emulator-5554 device
4. Appium сервер
В отдельном окне:

bash
appium
Проверка статуса: http://127.0.0.1:4723/status .

Настройка config.properties
src/test/resources/config.properties:

text
# Web
web.base.url=https://ru.wikipedia.org
web.browser=chrome
web.timeout.seconds=10

# Mobile
mobile.platform.name=Android
mobile.platform.version=16
mobile.device.name=emulator-5554
mobile.automation.name=UiAutomator2

mobile.appium.server.url=http://127.0.0.1:4723

mobile.app.package=org.wikipedia
mobile.app.activity=org.wikipedia.main.MainActivity
mobile.app.path=   # пусто, если приложение уже установлено
Методы в TestConfig читают эти значения и формируют capabilities для WebDriver и AndroidDriver.​

Запуск тестов
Web‑тесты
bash
mvn clean test -Pweb
Выполняется testng-web.xml (класс com.automation.web.tests.WikipediaWebTests).

Mobile‑тесты
bash
mvn clean test -Pmobile
Выполняется testng-mobile.xml (класс com.automation.mobile.tests.WikipediaMobileTests).

Комбинированный suite (опционально)
Можно создать testng-all.xml и использовать профиль -Pall, чтобы запускать web + mobile одним прогоном.​

Основные сценарии
Web
Проверка отображения главной страницы.

Поиск статьи и проверка заголовка.

Переход по ссылке «Заглавная страница».

Переход на страницу логина и проверка заголовка.

Mobile
Запуск приложения и проверка главного экрана.

Поиск статьи по ключевому слову и открытие первой статьи.

Проверка заголовка статьи.

Скролл и работа с оглавлением.

Поиск несуществующей статьи и проверка реакции приложения.​
