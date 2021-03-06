Разбираем вопросы по Python.
---
---

Существуют разные типы, mutable - может изменяться, не может 
изменяться - immutable.

---

Длинна идентификатора может быть любой, как латиница так и кирилица, числа
и нижнее подчеркивание.

---   

`dir()` - выводит все что есть у обьекта, все его сущьности, как методы так 
и атрибуты, вывод происходит просто в виде обычного списка. Просто говоря это 
выводит всю таблицу символов, что содержится в пространстве имен класса.

---

Использование функции `help()` выводит все что есть у обьекта, давая обзор 
на его строчку документации, методы и статические атрибуты класса.

---

Утиная типизация

---

Приглашение интерпретатора (interpreter prompt) - символы `>>>` 
интерпритатора, указывающий что тут можно писать код питона для исполненеия.

---

Функция `max()` может работать не только с поиском наибольшего числа, но 
и с поиском символа строки, что имеет наибольшее значение по кодировке 
Unicod:
    
```python
    string1 = "flyiNg"
    string2 = "flyiNgz"
    print(f'{string1} : ', max(string1))
    print(f'{string2} : ', max(string2))

    # Вывод
    # flyiNg :  y
    # flyiNgz :  z
```

---

Весь список можно разом превратить в удобочитаемую строчку, при помощи 
метода `join()`

---

Тред и его жизненный цикл: instance start sleep join

---

Словарь можно создать тремя способами: литералами {}, функцией dict(),
и генератором словарей `comprehension`

---

Сравнение операторами `> >= == < <= !=` на числа понятны, сравнения 
таким же образом на строки как работает ? 

---

Логические операторы `and`, `or`, `not`.

---

Оператор принадлежности `in` и `not in`

---

Операторы тождественности `is`, `is not`

---

Побитовые операторы: `& | ^ ~ << >>` 

---

docstring - Строки документации, строка что становться атрибутом `__doc__`
обьекта, присвоить ее можно классам и функциям, определяестя как первая 
строчка в обьекте.

---

Пример рекурсии, при счете Факториала:

```python
        def facto(n):
            if n == 1:
                return 1
            return n * facto(n - 1)

        print(facto(4))

        # Вывод
        24
```

---

Что такое оператор контроля последовательности (control flow statement)?

---

Один из возможных способов мнежественного присвоения:

```python
    a = b = c = 3
    print(a, b, c)

    # Вывод 
    # 3 3 3 
```

---

Механизм передачи по ссылке и по значению ? 

---

Когда в блоке try-except исполняется элемент else? блок else исполняется 
когда блок try не выдает исключения.

---

Что такое PYTHONPATH ? 

---

    x=[‘ab’,’cd’]
    print(len(map(list,x)))

---

remove() - удаляет элементы на основе их значения, del по позиции элемента.

---

Какие различия есть между методами для списков append() и extend()?

append() - добавляет элемент в конец списка, а extend() добавляет в конец 
итерируемый обьект, к примеру может добавить в конец списка, еще один список. 

---

Что случится, если не обработать ошибку в блоке except?

Ошибка отправится в стандартный вывод sys.stderr, но это поведение можно 
переопределить, сделав выводом скажем файл.

---

Как можно преобразовать целое число (integer) в символ Unicode? 

Это можно сделать при помощи спец функции `chr()`

---

Эта запись не создаст кортежа, только число, и скобки на это ни как 
не повлияют.

```python
    b = (1)
    print(b)
```

Чтобы создать именно кортеж, требуется указать более одного элемента,
через запятую.

```python
    b = (1,)
    print(b)
```

---

3 Способа удалить пробелы из строчки: 

```python
    string = 'aaa bbb ccc ddd eee'

    # Первый способ
    string1 = string.replace(" ", "")
    print(string1)

    # Второй способ
    string2 = ''.join([elem for elem in string if elem != " "])
    print(string2)

    # Третий способ
    string3 = ''.join(string.split())
    print(string3)
```

---

Функция `shuffle()` из модуля `random` перемешивает содержимое списка
в рандомном порядке.

---

enumerate - метод для итерации по последовательностям, таким как list,
tuple, set. Возвращает кортеж из ключа:значения не подходит для итерации по 
    словарям.

---

dict.items() - Возвращает кортеж из ключа:значения для словарей. 

---

Вывести елочку символов.

```python
        for i in range(1, 6):
        for j in range(1, 1+i):
            print('*', end='')
        print('\n')

        # Вывод
        # *
        # **
        # *** 
        # и тд ...
```

---

Когда использовать while в место for ? при простых циклах, и когда не 
нужно итерир по элементам обьекта. 

---

Метод get() вернет занчение по ключу если есть если нету то None, или
значение по умолчанию, ошибки по ключу не дает если этого ключа нету.

---

Массив array модуля NumPy работает быстрее лучше и удобнее чем обычный
список, и потребляют меньше памяти.

---

При установке ошибка типа `No matching installation found`

---

Динамическая загрузка модуля возможна при помощи модуля importlib

---

Генератор задает последовательность а итератор возвращает один обьект 
за раз, во время процесса итерации.

---

Тонкие различия между генератором и итераторм - генер имеет 
последовательность, в то врем как итератор использует функции 
iter() и next(). Генератор задается либо через собственную функциию
с yield или при помощи (генератора)

---

Monkey Patching - обезьяний патч

Это динамическое изменение части кода, класса или модуля прямо во время 
выполнения, это позволяет изменять работу модулей во время исполнения не 
меняя исходный код.

Может потреб при тестировании или быстром исправлении кода.

```python
    from pkg.module import MyClass

    def sayhello(self):
        print("Hello")
    
    MyClass.sayhello = sayhello
```

















