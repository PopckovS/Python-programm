Упаковка и распаковка
---

Когда мы передаем в функцию ряд неименованных аргументов, эти аргументы 
приходят в функцию в качестве обьедененного кортежа, это называется
упаковкой и указываетяся она при помощи символа звездочки `*args` 

Но есть и обратный процесс, распаковка, это процесс когда мы из структуры
изымаем все ее элементы, то есть тут эти переменные уже не обьеденены
некой структурой, просто ряд переменных, вот пример:

```python
    def function_1(*args):
        print('Пример с распаковкой:')
        print(type(args))
        print(*args)

    def function_2(*args):
        print('\nПример без распаковки:')
        print(type(args))
        print(args)

    function_1(1,2,3,4)
    function_2(1,2,3,4)

    # Вывод
    
    # Пример с распаковкой:
    # <class 'tuple'>
    # 1 2 3 4
    
    # Пример без распаковки:
    # <class 'tuple'>
    # (1, 2, 3, 4)
```

---

Интересное о присвоении данных аргументам функции
---

Когда мы имеем список, на него есть ссылка через имя переенной, но когда мы 
передаем этот список в функцию, для функции создается ее локальная память,
и поскольку список передается по ссылке, то теперь на наш список есть 2 ссылки,
одна ссылается из вне из внешнего кода, а другая ссылка ссылается на список 
изнутри функции.

Так изменение списка внутри функции повлияет на сам список и из вне, ибо 
список один, просто на него 2 ссылки, из вне и изнутри.

Но, опять же, если внутри функции мы сделаем присвоение типа:

```python
    my_list = [1,2,3]
    
    def func(my_list):
        my_list = my_list + [4, 5]

    func(my_list)
```

То в таком случае, новый my_list в нутри функции уже больше не будет ссылаться 
на внешний список, и его изменение не повлияет на внешний список. 