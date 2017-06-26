# Quiz

## Система для проведения интеллектуальных игр

### [Демо](http://algorithms.site/quiz/) 

Логин: admin

Пароль: admin

### Регистрация пользователя

Запустите в консоли `php register.php` и следуйте инструкциям

### Кое-что о структуре каталогов

`valuers` - каталог, содержащий оценивающие скрипты

`data/competitions/<competitoinId>/media` - каталог, содержащий все медиафайлы соревнования

### Как писать оценивающие скрипты

Оценивающий скрипт должен представлять из себя файл, в котором переменной `$calculate` 
присваивается функция двух аргументов, первый из которых - массив `$answers[$questionId]`,
содержащий массив объектов, содеражащих поля: `timestamp` - время отправки ответа (unix time in ms),
`team` - id команды, `results` - массив из нолей и единиц, длина которого равна количеству подзадач,
`0` означает неверный ответ на соответствующую подзадачу, `1` - верный.

Второй аргумент функции - объект `$quiz`. В оценивающих скриптах требуется поле
`$quiz->questions[$questionId]->scores` - массив объектов позадач, имеющих два поля: `title`
и `score` - название и стоимость подзадачи соответственно.

Функция должна возвращать массив вида `$res[$teamId] = $score`, т.е. сопоставляющий каждому
id команды кол-во баллов, которые она набрала в данном блоке.

[Пример оценивающего скрипта](valuers/sum.php)