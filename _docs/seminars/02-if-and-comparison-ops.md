---
title: 2 &mdash; Условия и операторы сравнения
permalink: /02/
---

# Условия (if, else, elif) и операторы сравнения


# На прошлом занятии

- `git` и github - где, что и как
- `установка` python
- базовые арифметические `операции`
- программа (`скрипт`) на python - всего лишь текстовый файл
- функция вывода данных на обозрение общественности - `print()`
- контейнеры для хранения данных - `переменные`
- базовые числовые типы данных - `int` и `float`
- строковый тип данных `str`
- способ перевести один тип в другой: `int('5') -> 5`


# Лирическое отступление про ввод данных и преобразования типов

На прошлом занятии мы научились выводить данные с помощью функции `print()`. Например, чтобы вывести число 5 на экран нужно написать в интерпретаторе `print(5)`, и он сделает свое дело.

Но что, если нужно что-то **ввести** в программу из внешнего мира? Например, если наш самописный калькулятор умеет складывать 2 числа и выводить ответ, то как ввести эти самые 2 числа? На помощь придет функция `input()`. Попробуем написать вышеописанный калькулятор.

> *Функции `input()` можно передать в качестве аргумента строку, которую увидит пользователь перед вводом.*

```python
>>> a = input('Введите число a: ')
>>> b = input('Введите число b: ')
>>> print(a + b)
```

![](https://pp.userapi.com/c852224/v852224115/190dc/Hl9qKjrjKI8.jpg)

Как видно из примера, что-то пошло не так. Вместо заветных 46 после сложения 12 и 34 мы получили 1234. Все дело в типах данных. Функция `input()` всегда считывает данные в виде строки. Так и в примере она считала 12 и 34 как 2 строки и просто «слепила» их вместе. Мы же хотим складывать числа. Чтобы все работало хорошо, нужно выполнить **преобразование типов данных**.

В данном случае можно сделать вот так:

```python
>>> a = int(input('Введите число a: '))
>>> b = int(input('Введите число b: '))
>>> print(a + b)
```

![](https://pp.userapi.com/c852224/v852224115/190e6/dm_7vxUgfPc.jpg)

То, чего мы и хотели. 

Преобразовывать можно не только строку в целое число, но и наоборот. Вот несколько допустимых преобразований:

![](https://pp.userapi.com/c852224/v852224422/1b949/s1fycWM9Fj8.jpg)

> *В примере мы используем функцию `type()`. Как должно быть понятно из её названия, она выяснят тип переменной. Возвращает она что-то
> страшное вида `<class 'str'>`. Сейчас не стоит вникать почему так. Нам
> важно, что преобразование прошло правильно и получился тип `str`.*

Как вы уже поняли, чтобы преобразовать что-то во что-то, надо взять и вызвать функцию, совпадающую по имени с названием типа данных. В нашем примере это `str()`, `int()` и `float()`.


# Условия

Все рассматриваемые нами ранее программы имели линейную структуру — программа просто выполняла инструкции одну за другой сверху вниз. При этом никаких способов повлиять на ход выполнения у нас не было (разве что только на уровне выводимых на экран параметров). 
Также важно то, что наши предыдущие программы обязаны были выполнить все инструкции сверху вниз, в противном случае они бы завершались ошибкой.

Теперь предположим, что мы хотим определить абсолютное значение любого числа. Наша программа должна будет напечатать сам `x` в случае, если он неотрицателен и `-x` в противном случае. Линейной структурой программы здесь не обойтись\*, поэтому нам на помощь приходит инструкция **if (если)**. Вот как это работает в питоне:

```python
>>> # Ввод данных с преобразованием типа
>>> x = int(input())
>>>
>>> if x > 0:
...     print(x)
>>> else:
...     print(-x)
```

> \* На самом деле в python есть функция [`abs()`](https://docs.python.org/3/library/functions.html#abs), с помощью
> которой можно взять модуль числа. Но в качестве примера
> использования конструкции `if` и так хорошо.

Разберем этот кусочек кода. После слова `if` указывается проверяемое условие `(x > 0)`, **завершающееся двоеточием** (это важно). После этого идет блок (последовательность) инструкций, который будет выполнен, если условие истинно. В нашем примере это вывод на экран величины `x`. Затем идет слово `else` (иначе), также **завершающееся двоеточием** (и это важно), и блок инструкций, который будет выполнен, если проверяемое условие неверно. В данном случае будет выведено значение `-x`.

Обратите особенное внимание на отступы во фрагменте кода выше. Дело в том, что в питоне, для того, чтобы определить, какой именно код выполнить в результате того или иного условия используется как знак двоеточия (в строке с самим условием), так и отступы от левого края строки.

> Небольшая ремарка относительно табуляции.
> Мы используем **4 пробела**!
> В современных текстовых редакторах при нажатии на tab автоматически
> вставляется 4 пробела. Не надо жать 4 раза кнопку space как вот
> [тут](https://www.youtube.com/watch?v=AXLoRpKnK8U). Никакой войны,
> никаких табов. Просто **4 пробела**.

Во многих других языках вместо отступов используются конструкции, явно указывающие на начало (begin или открывающаяся фигурная скобка в Си) и конец инструкций, связанных с условием (end или закрывающаяся фигурная скобка в Си). Отступы же выполняют примерно ту же роль, но и заодно делают код более читаемым, позволяя читающему быстро понять, какой именно код относится к условию.

Таким образом, условные конструкции в питоне имеют следующий общий вид:

    if Условие:
        блок инструкций, в случае если условие истинно
    else:
        блок инструкций, в случае если условие не выполняется

Вторая часть условной конструкции (та, что с else) может и отсутствовать, например так:

```python
>>> x = int(input())
>>>
>>> if x < 0:
...     x = -x
... 
>>> print(x)
```

Эта программа тоже выведет абсолютное значение x, как и та, что была ранее.


# Операторы сравнения

Все операторы сравнения в питоне достаточно интуитивны. Вот список основных:

`>` - больше. Условие истинно, если то, что слева от знака больше того, что справа.<br>
`<` - меньше. Условие истинно, если то, что слева от знака меньше того, что справа.<br>
`>=` - больше либо равно.<br>
`<=` - меньше либо равно.<br>
`==` - в точности равно.<br>
`!=` - не равно.<br>


# Вложенные условные инструкции

Условия могут быть вложены одно в другое, чтобы реализовывать еще более сложную логику, например:

```python
>>> a = int(input())
>>> b = int(input())
>>>
>>> if a > 0:
...     if b > 0:
...         print("a, b > 0")
...     else:
...         print("a > 0, b < 0")
... else:
...     if b > 0:
...         print("a, b < 0")
...     else:
...         print("a < 0, b > 0")
...
```

Главное, не забывать **отступы** и **двоеточия**.


# Тип данных `bool`

Операторы сравнения возвращают значения специального логического типа bool. Значения логического типа могут принимать одно из двух значений: `True (истина)` или `False (ложь)`. 

Если преобразовать логическое `True` к типу `int`, то получится `1`, а преобразование `False` даст `0`. При обратном преобразовании число `0` преобразуется в `False`, а любое ненулевое число в `True`. При преобразовании `str` в `bool` пустая строка преобразовывается в `False`, а любая непустая строка в `True`.

Рассмотрим несколько примеров:

![](https://pp.userapi.com/c852224/v852224429/1aa74/ghVbxNTsntY.jpg)

![](https://pp.userapi.com/c852224/v852224429/1aa6a/fxiwTsHVUx8.jpg)

![](https://pp.userapi.com/c852224/v852224429/1aa88/GBrAl2T7as4.jpg)

> Обратите внимание, ключевые слова `True` или `False` пишутся с
> **большой буквы**. Если написать их с маленькой, то python подумает, что это переменная, попытается её найти и сломается, когда не найдет
> `:(`. А если вы вздумаете называть свои переменные `false` или `true`, то сдать зачет 
> по курсу вам не светит `:)`. Учитесь сразу хорошему стилю программирования.

![](https://pp.userapi.com/c852224/v852224125/1ab54/6pjR8a9aw8k.jpg)


# Логические операторы

Если мы хотим проверить два или более условий за раз, мы можем воспользоваться операторами `and`, `or` или `not`. Вот как они работают:

`and` (логическое И) возвращает истину (`True`) только в случае если оба условия по отдельности верны (тоже возвращают `True`)<br>
`or` (логическое ИЛИ) вернет истину в случае, если хотя бы одно из условий верно.<br>
`not` (логическое НЕТ) возьмет результат условия и "обратит" его. То есть, если результат условия `True`, то `not` примененный к этому условию вернет `False` и наоборот.<br>

Давайте посмотрим как это работает на примере. Код ниже проверяет, что хотя бы одно число из двух нацело делится на 10 (кончается на 0) и если так, то печатает **YES**, а если нет, то печатает **NO**:

```python
>>> a = int(input())
>>> b = int(input())
>>>
>>> if a % 10 == 0 or b % 10 == 0:
...     print('YES')
... else:
...     print('NO')
...
```

Пусть теперь мы хотим проверить, что числа a и b должны быть еще и обязательно больше нуля:

```python
>>> a = int(input())
>>> b = int(input())
>>>     
>>> if (a % 10 == 0 and a > 0) or (b % 10 == 0 and b > 0):
...     print('YES')
... else:
...     print('NO')
...
```

Как видите, мы можем не только использовать `and` и `or` в одном `if`, но и группировать условия скобками для того, чтобы явно обозначить приоритет вычисления условий.

Посмотрим пример с `not`. Пусть мы хотим проверить, что число a - положительное, а число b - неотрицательное.
Это можно проверить вот таким условием:

```python
>>> if a > 0 and not (b < 0):
...     pass
...
```

> Оператор `pass` очень полезен, когда нужно ничего не делать. Если его
> не поставить, то будет синтаксическая ошибка. А так, код считается правильным!

Кстати, `not (b < 0)` можно было бы и заменить на `b >= 0` и код бы работал точно так же.

# Конструкция elif

Иногда писать конструкции `if-else` долго и утомительно, особенно если приходится проверять много условий разом. В этом случае на помощь придет `elif` (сокращение от else if). По сути `elif` позволяет существенно упростить конструкцию ниже:

```python
>>> if a > 0:
...     pass
... else:
...     if b > 0:
...         pass
...
```

И сделать ее вот такой:

```python
>>> if a > 0:
...     pass
... elif b > 0:
...     pass
...
```

Обратите внимание, мы избавились от одного уровня вложенности. То есть, сам код стал более читаемым, но при этом нисколько не проиграл в функциональности. Разумеется, конструкции типа `if-elif` могут завершиться и блоком `else`, например так:

```python
>>> if a > 0:
...     pass
... elif b > 0:
...     pass
... elif c > 0:
...     pass
... else:
...     pass
...
```

# Задача: знак числа

В математике есть функция [sgn](https://ru.wikipedia.org/wiki/Sgn), показывающая знак числа. Она определяется так: если число больше 0, то функция возвращает 1. Если число меньше нуля, то функция возвращает -1. Если число равно 0, то функция возвращает 0. Реализуйте данную функцию — для введенного числа выведите число, определяющее его знак. Используйте операторы сравнения и конструкцию `if-elif-else`.

Возможное решение:

```python
>>> x = int(input())
>>> 	
>>> if x > 0:
...     print(1)
... elif x < 0:
...     print(-1)
... else:
...     print(0)
...
```

# Задача: високосный год

Дано натуральное число. Требуется определить, является ли год с данным номером високосным. Если год является високосным, то выведите YES, иначе выведите NO. Напомним, что в соответствии с григорианским календарем, год является високосным, если его номер кратен 4, но не кратен 100, а также если он кратен 400.

Возможное решение:

```python
>>> year = int(input())
>>> if (year % 4 == 0 and year % 100 != 0) or (year % 400 == 0):
...     print('YES')
... else:
...     print('NO')
...
```	    

# ДЗ

Вам надо написать на питоне программу, которая спрашивала бы у пользователя три числа (a, b и c), а дальше, в зависимости от номера Вашего варианта, сообщала бы пользователю, обладают или не обладают введённые числа некоторыми свойствами. Вот общий список свойств:

1. `a` и `b` в сумме дают `c`
2. `a` умножить на `b` равно `c`
3. `a` даёт остаток `c` при делении на `b`
4. `c` является решением линейного уравнения `ax + b = 0`
5. `a` разделить на `b` равно `c`
6. `a` в степени `b` равно `c`.

Если у Вас
- 1-й вариант, программа должна проверять свойства (2) и (4)
- 2-й — (3) и (4)
- 3-й — (1) и (5)
- 4-й — (2) и (5)
- 5-й — (3) и (5)
- 6-й — (5) и (6)
- 7-й — (1) и (4)

То есть если у Вас, например, 3-й вариант, то Ваша программа должна проверять, дают ли `a` и `b` в сумме число `c` и получится ли `c`, если `a` разделить на `b`, и сообщать об этом.

Выполните задание пройдя по ссылке в GitHub Classroom:

- 1 группа: дедлайн 19.10.2018 23:59 <https://classroom.github.com/a/UBN-r5R3>
- 2 группа: дедлайн 14.10.2018 23:55 <https://classroom.github.com/a/Xy9aD9Kv>
- 3 группа: дедлайн 14.10.2018 23:55 <https://classroom.github.com/a/C7bvbOG2>
- 4 группа: дедлайн 16.10.2018 23:55 <https://classroom.github.com/a/jEtSOjIU>

# Ссылки по теме

* [http://pythontutor.ru/lessons/ifelse/](http://pythontutor.ru/lessons/ifelse/)
* [http://pythonicway.com/python-conditionals ](http://pythonicway.com/python-conditionals)
