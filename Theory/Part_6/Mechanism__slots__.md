Механизм `__slots__`
---
---
У обьектов есть специальный атрибут `__dict__` который содержит
в себе словарь со всеми атрибутами обьекта, этот атрибут определен 
по дефолту.

Также по мимо этого мы можем сами обьявить в классе специальный 
атрибут `__slots__ = ['x', 'y', 'z']` создание этого атрибута
автоматически непозволяет использовать `__dict__` по скольку 
атрибут `__slots__` фиксированный поиск элеементов в нем статичны,
это дает след преимущества:

1) У обьекта можно создавать только те атрибуты которые 
   перечислены в `__slots__`
2) По скольку количество элементов фиксированное поиск элементов 
проходит значительно быстрее.
   
Каждый элемент в `__slots__` хранится в заранее отведенном месте
и по этому является **обьектом дескриптора**

Реализация этого механизма полность на языке `C` и потому очень 
эфективна.

Если всетаки нам требуется использовать `__dict__` совместно с 
`__slots__` то мы можем сделать это добавив `__dict__` а перечень
`__slots__`

Пример реализации:

```python
     class Point:

        __slots__ = ['x', 'y', '__dict__']

        def __init__(self, x, y):
            self.x = x
            self.y = y

        def setCoords(self, x, y):
            self.x = x
            self.y = y

        def getCoords(self):
            return self.__slots__


    pt = Point(10, 20)

    pt.x = 1
    pt.y = 2
    pt.z = 55

    print(pt.getCoords())
    print(pt.z)

    # Вывод
    # ['x', 'y', '__dict__']
    # 55
```

Также не льзя обьявлять в слотах переменную класса, это 
даст ошибку.

    STATIC_NAME = 'Статичное название'
    __slots__ = ['x', 'y', '__dict__', STATIC_NAME]

---

Атрибут __slots__ 
---

По дефолту класс реализует атрибут __dict__ это словарь в котором он 
будет содержать все атрибуты обьекта.

Можно определить список или кортеж __slots__ как атрибут класса, и обьявить 
в нем названия всех переменных которые можно обьявлять и использовать в обьекте
такого класса, при этом атрибут __dict__ автоматически не создается.

Это позволяет экономить память в программе, у обьектов и атрибутов есть такой 
метод как `__sizeof__()` который возвращает размер затрачиваемой памяти на 
хранение данного элемента:

```python
        class One:
        """Заменяет __dict__ атрибутом __slots__"""
        __slots__ = ['x', 'y']

        def __init__(self, x, y):
            self.x = x
            self.y = y

        def get_coord(self):
            return self.x, self.y

    class Two:
        """Имеет атрибут __dict__"""

        def __init__(self, x, y):
            self.x = x
            self.y = y

        def get_coord(self):
            return self.x, self.y

    x1 = One(10, 20)
    x2 = Two(100, 200)

    print('Класс с __slots__ :', x1.__sizeof__())
    print('Класс с __dict__ :', x2.__sizeof__(), x2.__dict__.__sizeof__())

    # Вывод
    # Класс с __slots__ : 32
    # Класс с __dict__ : 32 88
```

Как можно увидеть, класс у которого есть атрибут __dict__ занимает на 88 байт 
памяти в кто время как у другова класса, атрибута __dict__ вовсе нету и памяти 
он не занимает вообще. 

---

Оптимизация кода
---

1) Использование спец атрибута __slots__ который может применять list или tuple
их потребление памяти ниже чем у dict так образ снижается потребление памяти.
   

```python
    print('dict().__sizeof__() = ', dict().__sizeof__())
    print('list().__sizeof__() = ', list().__sizeof__())
    print('tuple().__sizeof__() = ', tuple().__sizeof__())
    print('set().__sizeof__() = ', set().__sizeof__())

    # Вывод
    # dict().__sizeof__() =  216
    # list().__sizeof__() =  40
    # tuple().__sizeof__() =  24
    # set().__sizeof__() =  200
```

2) Использование слабых ссылок, слабые ссылки в отличии от обычных ссылок, 
говорят сборщику мусора что обьекты на которые ссылается слабая ссылка можно 
удалять в отличии от обычных ссылок которые.