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

1. Обнаружил error в консоли браузера => заключил содержание import в скобки. Открыл [документацию](https://tech.yandex.ru/maps/doc/jsapi/2.1/quick-start/index-docpage/) Карт => перенес скрипт в хед, добавил контейнеру карты размеры, теперь карта отображается и занимает весь экран.
1. Заключал в комментарии и консоль лог каждую функцию и изучал поведение сверился с информацией по Object_manager, понял, что метки создаются, но не отображаются. Добавил метки на карту с помощью geoObjects. Теперь метки отображаются в Иране. Супер
1. Ошибка с отображением должна быть в другом модуле, ибо в этом все с виду в порядке. Зашел в mappers, решил свапнуть местами широту и долготу. Теперь метки переехали в столицу
1. Для наглядности отображения пинов увеличил gridSize до 128. Убрал пресет цвета кластера, теперь в кластере отображаются как исправные(синим), так и неисправные станции(красным). Чтобы проверить что цвет меток правильный я зашел в DevTools - Network - XHR - stations, и через cmd+f проверил количество станиций с isActive: false, настройка цвета пинов лежит в файле mappers.js. Фильтрация работает
1. Осталось отобразить содержимое при клике на базовую станцию. Консоль говорит, эррор, destroy = null. Закомментил geoObjectBalloonContentLayout: getDetailsContentLayout(ymaps) в map.js/objectManager и ошибка пропала, должно быть ошибка в модуле details. Зашел в него, заметил, что используется this в стрелочной функции, а значит контекст исполнения не тот. Исправил контекст заменив стрелочную функцию на функциональное выражение.
1.  Почитал [документацию](http://www.chartjs.org/docs/latest/getting-started/usage.html) ChartJS, заменил неверный адрес импорта из модуля chart.js, количество скрытых модулей при сборке увеличилось и окно графика теперь появляется без ошибок в консоли.
1. Заметил, что в окне графика стоит максимальная высота 0 по оси Y. В файле XHR в графе chart все значения выше 0, значит график нам не виден из-за максимального значения. Убрал его - вуаля, все работает как нужно.
1. Лишний код: обнаружил, что функция getPopupContent экспортируется, но в приложении нигде не используется - модуль popup.js не нужен, удалил его.
1. Прогнал файлы через ESLint, привел всё к единому кодстайлу.
