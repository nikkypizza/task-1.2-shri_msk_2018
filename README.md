# Задание 1 — найди ошибки

Код содержит ошибки разной степени критичности. Некоторые из них — стилистические, а другие — даже не позволят вам запустить приложение. Вам нужно найти все ошибки и исправить их.

Пункты для самопроверки:

1. Приложение должно успешно запускаться.
1. По адресу http://localhost:9000 должна открываться карта с метками.
1. Должна правильно работать вся функциональность, перечисленная в условиях задания.
1. Не должно быть лишнего кода.
1. Все должно быть в едином codestyle.

При каждом запуске тестовые данные генерируются заново случайным образом.

### Процесс отладки:

1. Обнаружил error в консоли браузера => заключил содержание import в скобки. Открыл [документацию Карт](https://tech.yandex.ru/maps/doc/jsapi/2.1/quick-start/index-docpage/) => перенес скрипт в хед, добавил контейнеру карты размеры, теперь карта отображается и занимает весь экран.
2. ...
