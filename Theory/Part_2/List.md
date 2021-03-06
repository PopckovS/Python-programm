Списки
---

Списки - внутри являются массивами, просто называются списками, но это
массива не списки как в других языках, скорость доступа к элементам по
индексам происходит за константу и получение длинны списка за константу,
также списки как и строки можно канкатенировать при помощи символа плюса.
Списки стараются использовать для хранения значений одинаковых типов.

---

## list Списки
Списки это последовательности, так что они имеют схожий способ доступа, 
вывести список можно обычной функцией `print()`.

```python
    my_list = ['one', 'two', 2, 3.14, 1.618]
```

Мы можем добавить новый элемент в список, двумя разными способами, к
примеру так:

```python
    my_list = ['one', 'two', 2, 3.14, 1.618]

    my_list.append('new var')
    my_list = my_list + ['new var']
```
    
Что такое строка ? строка это тоже последовательность, и реализованная в виде 
чего-то похожего на кортеж. При добавлении нового элемента не методом 
`.append()` а при помощи обычного оператора `+` то есть разница между 
добавление строки и списка в котором есть строка, если добавляем список с одним 
элементом то все сработает как с методом `.append()` но если мы просто 
добавляем строку, то вся строка будет разделена на элементы и обавлена в
качестве списка, вот как это выглядит:

```python
    my_list1 = ['one', 'two', 2, 3.14, 1.618]
    my_list2 = my_list1[:]

    my_list1 += 'new var'
    my_list2 += ['new var']

    # Вывод
    # ['one', 'two', 2, 3.14, 1.618, 'n', 'e', 'w', ' ', 'v', 'a', 'r']
    # ['one', 'two', 2, 3.14, 1.618, 'new var']       
```
    
Копирование одного списка в другой:

```python
    my_list1 = ['one', 'two', 2, 3.14, 1.618]
    my_list2 = my_list1[:]
```
    
Проход по списку
---
Обычно для того чтобы пройтись по списку, нам требуется 2 возможных 
варианта, либо пройтись именно по элементам списка, либо пройтись циклом
такое количество раз сколько элементов в списке у нас имеется с допуском
к каждому элементу по его индексу.

1) Пройтись именно по каждому элементу списка:

```python
      my_list = ['один', 'два', 'три', 'четыре', 'пять']
      for elem in my_list:
         print(elem)
```
         
2) Пройтись циклом столько сколько есть элементов в списке, с допуском к
каждому элементу по его индексу:
   
```python
      my_list = [1, 2, 3, 4, 5]
      for i in range(len(my_list)):
          my_list[i]+=5
          print(my_list)
```

---

Методы списков
---
1) append() - Добавляет элемент в конец списка
2) pop() - Удаляет последний элемент из списка, или элемент по переданному 
   индексу, при этом удаленный элемент будет возвращен в переменную.
3) reverse() - Меняет порядок элементов списка на обратный
4) sort() - Сортирует в Алфавитный/По возрастанию порядок

---

 Генерация списка
---
Это своего рода петля for внутри скобок.

      first_col = []
---

Методы списков
---

count(value) - Возвращает количество раз сколько значение 
встречается в списке.

```python
    my_list = [1,2,3,4,5,6]
    print(my_list.value(3))

    # Вывод
    # Сколько раз в списке встречается значение '3'
    # 1
```

---

Вывод элементов списка
---

Когда мы хотим вывести все элементы списка, используя метод `print` получаем вывод
со скобками, также будет и при использовании метода `repr` для красивого вывода можно 
использовать метод строк `join`

Как помним `join` это метода строк который принимает в себя некую последовательность 
и выводит эту последовательность, элемент за элементом, соедененные вместе при помощи 
той самой строки у которой этот метод вызывается.

Так что для красивого вывода без скобок можно использовать метод строк `join`

К примеру так:

```python
    my_list = ['первый', 'второй', 'третий', 'четвертый']
    print('Вывод списка методом print: ', my_list)
    print('Вывод списка методом join: {list}'.format(list=' , '.join(my_list)))

    # Вывод
    # Вывод списка методом print:  ['первый', 'второй', 'третий', 'четвертый']
    # Вывод списка методом join: первый , второй , третий , четвертый
```

---

list присвоение по ссылке и по значению
---

Когда есть список с которым мы хотим сделать ряд изменений, есть одна тонкость,
для добавления элемента в список используем метод `.append()` если требуется
добавить последовательность к концу списка, то используем метод `.extend(list)`

Если мы соединяем список с другим списком при помощи сложения `+` и присвоим 
это другой переменной, то будет создано полностью новое значение, присвоено 
другой переменной, и это уже 2 разных обьекта.

```python
    my_list_1 = [1, 2, 3]
    my_list_2 = my_list_1 + [1, 2, 3]
    print(my_list_1, id(my_list_1))
    print(my_list_2, id(my_list_2))

    # Вывод
    # [1, 2, 3] 140529396469256
    # [1, 2, 3, 1, 2, 3] 140529396503304
```

---
Срвнения списков
---

Списки явл изменяемым типом данных, так что 2 переменные явл разными
обьектами, так что ответ будет `False`

```python
    a = [1, 5]
    b = [1, 5]
    print(a is b)
    
    # Вывод
    # False
```