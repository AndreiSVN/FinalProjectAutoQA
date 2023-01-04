# FinalProjectAutoQA
Проект содержит файлы необходимые для проведения тестирования нового интерфейса авторизации в личном кабинете от заказчика:
1)	Ссылка на Excel-файл с набором тест-кейсов и описанными багами.
2)	Ссылка на Word-файл с результатами проверки документации (Требования по проекту, желтым выделены непонятные места, красным шрифтом написаны комментарии и замечания).
3)	Файл conftest.py содержит конфигурационные данные для проведения автотестов.
4)	Файл base_page_class.py содержит базовый класс страницы и методы для проведения тестирования.
5)	Файл authentication_page.py содержит класс страницы авторизации на сайте Ростелеком Информационные Технологии необходимый для проведения тестирования.
6)	Файл registration_page.py содержит класс страницы регистрации на сайте Ростелеком Информационные Технологии необходимый для проведения тестирования.
7)	Файл elements_set.py содержит класс методов необходимых для взаимодействия с веб-элементами на сайте Ростелеком Информационные Технологии.
8)	Автотесты в папке test_suites проверяют:
•	авторизацию для входа в личный кабинет – authentication_suite.py;
•	регистрацию на сайте – registration_suite.py
В тест-кейсах и автотестах применялись следующие техники тест-дизайна:
1.	«состояние-переход» для авторизации по временному коду и восстановления пароля;
2.	метод граничных значений и классы эквивалентности для полей ввода:
2.1 «Имя» и «Фамилия» - граничные значения 2 символа и 30 символов, значения с 1-, 3-, 15-, 29-, 31- символом, значение с дефисом, а также с латинскими буквами, XSS-инъекция, SQL-инъекция;
2.2 «E-mail или мобильный телефон» - значения с корректным и некорректным форматом адреса, номера телефона корректного формата «+7 и 11 цифр», «8 и 11 цифр» и «+375 и 9 цифр», «+7 и 10 цифр», «+7 и 12 цифр», «+375 и 8 цифр», «+375 и 10 цифр»;
2.3 «Пароль» - значения, состоящие из 7-, 8-, 20- и 21- символов, с/без - спецсимвол, заглавная буква, цифры, также с буквами кириллицы, XSS-инъекция, SQL-инъекция.
3.	технику попарного тестирования для формы авторизации.
Для более тщательного проведения автотестов требуется отключение «Капчи».

ВАЖНО: Тесты из файла registration_page.py не запускаются в самом файле. Запускаются только, если скопировать весь набор в authentication_page.py и запустить в этом файле. Причину установить не смог.
