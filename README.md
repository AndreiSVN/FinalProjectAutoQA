# FinalProjectAutoQA

Проект содержит файлы необходимые для проведения тестирования нового интерфейса авторизации в личном кабинете от заказчика:
1)	Excel-файл "Итоговый набор тест-кейсов и баг-репорты" с набором тест-кейсов и описанными багами. Ссылка на гугл-диск: https://docs.google.com/spreadsheets/d/16qEpFZGR0QR5jslC5n9NEZB6FOkUbiIf/edit?usp=sharing&ouid=111975222856008639943&rtpof=true&sd=true
2)	Word-файл "Требования_SSO_для_тестирования_анализ" с результатами проверки документации (желтым выделены непонятные места, красным шрифтом написаны комментарии и замечания). Ссылка на гугл-диск: https://docs.google.com/document/d/1h8yagmAhYNrFkg6XCFKUK8bBDyQKWT2m/edit?usp=sharing&ouid=111975222856008639943&rtpof=true&sd=true
3)	Файл conftest.py содержит конфигурационные данные для проведения автотестов.
4)	Файл base_page_class.py содержит базовый класс страницы и методы для проведения тестирования.
5)	Файл authentication_page.py содержит класс страницы авторизации на сайте Ростелеком Информационные Технологии необходимый для проведения тестирования.
6)	Файл registration_page.py содержит класс страницы регистрации на сайте Ростелеком Информационные Технологии необходимый для проведения тестирования.
7)	Файл elements_set.py содержит класс методов необходимых для взаимодействия с веб-элементами на сайте Ростелеком Информационные Технологии.
8)	Автотесты в папке test_suites проверяют:
-	авторизацию для входа в личный кабинет – authentication_suite.py;
-	регистрацию на сайте – registration_suite.py

В тест-кейсах и автотестах применялись следующие техники тест-дизайна:
1.	«состояние-переход» для форм авторизации по временному коду и восстановления пароля, потому что мы можем отследить правильность составленного тестового сценария и отследить возможные пробелы при переходах от одного состояния до другого;
2.	поскольку у нас есть конкретные требования к полям, приняем метод граничных значений и классы эквивалентности для полей ввода: 
    - «Имя» и «Фамилия» - граничные значения 2 символа и 30 символов, значения с 1-, 3-, 15-, 29-, 31- символом, значение с дефисом, а также с латинскими буквами, XSS- инъекция, SQL-инъекция;
    - «E-mail или мобильный телефон» - значения с корректным и некорректным форматом адреса, номера телефона корректного формата «+7 и 11 цифр», «8 и 11 цифр» и «+375 и 9 цифр», «+7 и 10 цифр», «+7 и 12 цифр», «+375 и 8 цифр», «+375 и 10 цифр»;
    - «Пароль» - значения, состоящие из 7-, 8-, 20- и 21- символов, с/без - спецсимвол, заглавная буква, цифры, также с буквами кириллицы, XSS-инъекция, SQL-инъекция.
3.	техника попарного тестирования для формы авторизации - тем самым проверяем все возможные комбинации параметров.

Для более тщательного проведения автотестов требуется отключение «Капчи».

Запуск автотестов рекомендуется выполнять в PyCharm IDE.

Что не получилось: создать автотест для проверки поля "Регион". Выпадающий список не имеет возможности программирования выбора, т.е. в HTML коде не предусматривается возможность получения всего списка и/или выбора определенного значения. На мой взгляд, существует только вариант ввода определенного значения и подтверждения путем клика на предложенный системой вариант. Однако, возникают сложности с передачей нужного значения в поле ввода (система странно реагирует на ввод), а также невозможно реализовать способ кликнуть на значение, которое расположено в определенном месте выпадающего списка.
