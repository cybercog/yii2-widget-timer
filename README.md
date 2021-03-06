# yii2-widget-timer
Simple timer widget for yii2-based applications

## Widget timer on jquery plugin.

Отображает время, прошедшее со старта timer в формате ЧЧ:ММ:СС где:
* ЧЧ - кол-во прошедших с момента запуска часов;
* ММ - кол-во прошедших с момента запуска минут;
* CC - кол-во прошедших с момента запуска секунд;
Может быть запущен автоматически и вручную, может быть остановлен, сброшен

## Установка

Предпочтительный способ установки через [composer](http://getcomposer.org/download/). Ознакомьтесь с требовния расширения и его зависимостями в [composer.json](https://github.com/aayaresko/yii2-widget-timer/blob/master/composer.json).
Для установки выполните

```
$ php composer.phar require aayaresko/yii2-widget-timer "dev-master"
```

или добавьте

```
"aayaresko/yii2-widget-timer": "dev-master"
```

в секцию ```require``` вашего `composer.json`.

## Использование

выполнить загрузку необходимых компонентов и подготовить видже

```php
use aayaresko\timer\Timer
Timer::widget([
    'options' => [
        'container' => '.timer',
        'manual' => true,
    ]
])
```

Инициализировать plugin с автоматическим запуском счётчика (рабочий экземпляр plugin будет доступен в глобальной области видимости под именем $.fn.timer.worker)

```php
    $.fn.timer.worker.init(true);
```

Управление plugin осуществляется через методы:
* container - селектор html элемента, в котором необходимо отобразить таймер (по умолчанию '.timer');
* hours – начать счёт часов с этого значение (по умолчанию '00');
* minutes – начать счёт минут с этого значение (по умолчанию '00');
* seconds – начать счёт секунд с этого значение (по умолчанию '00');

Управление plugin осуществляется через методы:
* init(value) - инициализирует таймер, оформит html-содержимое container в виде таймера (если value == false) или запустит таймер автоматически (если value == true), при этом, если таймер был ранее запущен автоматически остановит таймер и обнулит значения часов, минут, сукунд;
* go() - запустит таймер;
* stop(value) - остановит таймер сохранив текущие значение часов, минут, секунд (если value == false) или обнулит их (если value == true);
* flush() - сбросит таймер, обнулив значения часов, минут, секунд.

## License
**yii2-widget-timer** is released under the BSD 3-Clause License. See the bundled `LICENSE.md` for details.