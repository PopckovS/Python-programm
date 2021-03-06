## Python и ООП 1

### Маг метод __delattr__(self, item)
Метод вызывается при попытке удалить атрибут обьекта, а 
именно при использовании оператора `del` на атрибут обьекта.

При этом при попытке удалить атрибут обьекта которого не 
существует, ошибки не будет.

Пример реализации:

    class Point:
        def __init__(self, x, y):
            self.x = x
            self.y = y

        def __delattr__(self, item):
            print('Попытка удалить атрибут = ', item)
            del self.__dict__[item]

    pt = Point(10, 20)
    print(pt.__dict__)
    del pt.x
    print(pt.__dict__)

    // Вывод
    {'x': 10, 'y': 20}
    Попытка удалить атрибут =  x
    {'y': 20}


### Маг метод __setattr__(self, key, value)
Этот метод используется когда мы пытаемся присвоить обьекту не
существующего атрибута,ли при попытке переопределить значение уже 
существующего атрибута.

Интересно то что этот метод вызывается всегда, даже в момент 
инициализации обьекта, при присвоении начальных значений в 
методе `__init__()` он тоже вызыыватеся.

В самом методе `__setattr__` нельзя присваивать значение следующим
синтаксисом:

    self.name = x

Это вызовет повторный вызов самой функции `__setattr__` и приведет
к перенаполнению стека вызовов, и рекурсии.

Присваивать новое значение следует через спец атрибут `self.__dict__`
который содержит в себе все переменные обьекта в виде словаря.

Пример реализации:

    class Point:
        def __init__(self, x, y):
            self.x = x
            self.y = y

        def __setattr__(self, key, value):
            print("попытка присвоить несуще аргумент.")
            print('name=', key, ' value=', value)
            self.__dict__[key] = value

    pt = Point(10, 20)
    print('pt.__dict__ = ', pt.__dict__)
    pt.name = 30
    print('pt.__dict__ = ', pt.__dict__)
    pt.name = 55
    print('pt.__dict__ = ', pt.__dict__)
    
    //Вывод
    попытка присвоить несуще аргумент.
    name= x  value= 10
    попытка присвоить несуще аргумент.
    name= y  value= 20
    pt.__dict__ =  {'x': 10, 'y': 20}
    попытка присвоить несуще аргумент.
    name= name  value= 30
    pt.__dict__ =  {'x': 10, 'y': 20, 'name': 30}
    попытка присвоить несуще аргумент.
    name= name  value= 55
    pt.__dict__ =  {'x': 10, 'y': 20, 'name': 55}

### Маг метод __getattr__(self, item)
Магический метод, вызывается при попытки получить досступ к 
несуществующему атрибуту класса, в этом методе оможно перехватить 
этот процес и определить что именно возвращать когда пользователь
пытается получить несуществующий атрибут.

А можно определить поведение что при обращении именно к определенному
параметру, отдавать некотрые данные, или поднять ошибку.

    class Point:

        def __init__(self, x, y):
            self.__x = x
            self.__y = y

        def __getattr__(self, item):
            print('Запрошен атрибут с названием = ', item)
            if item == 'name':
                return 'Класс для представления точки на плоскости'
            else:
                raise AttributeError


    pt = Point(1, 2)
    print('Делаем обращение к несуществующему элементу')
    print(pt.name)
    print(pt.age)


### Интересное о вызове методов обьектов и классов
Когда мы передаем в функцию параметры, первый параметр это `self`
который представляет из себя сам обьект, этот метод можно вызывать 
у обьекта.

Также по мимо этого, этот же метод можно вызывать не только у 
обьекта но и как метод класса, только в качестве первого аргумента 
передать обьект этого класса, просто обычно Python делает это
автоматически, сдесь же мы делаем это в ручную.

    class Point:

        def __init__(self, x=0, y=0):
            self.x = x
            self.y = y

        def setCoords(self, x, y):
            self.x = x
            self.y = y

        def getCoords(self):
            return self.x, self.y

Есть 2 метода, геттер и сеттер, один кладет данные в обьект 
другой берет данные из обьекта, оба метода должны вызываться как
методы обьекта. Сделаем вызов как от обьекта так и от класса.

Следующие 2 примера одинаковы:

    pt1 = Point()
    pt1.setCoords(10, 20)
    print('pt1 = ', pt1.getCoords())

    pt2 = Point()
    Point.setCoords(pt2, 10, 20)
    print('pt2 = ', Point.getCoords(pt2))

### isinstance(obj, class)
Метод позвоялет проверить является ли обьект экземпляром класса.

    print(isinstance(m, MyClass))

    // Вывод
    True

По сути этот метод можно полностью заменить проверкой с условие:

    if type(m) == MyClass:
        print('yes')
    else:
        print('no')

    // Вывод 
    True

### Метод getattr(obj, name, default=True)
Метод позволяет получить значение переменной обьекта, первый арг
это сам обьект, второй это название переменной к которой мы хотим
обратиться, третий параметр дефолтно = True и даст ошибку если 
такого атрибута не существует, если учтановить в = False то ошибки 
не будет.

        class Point():
            x = 10
            y = 20
            def __init__(self):
                self.dinamic_x = 1
                self.dinamic_y = 2

        pt = Point()
        print(getattr(pt, 'dinamic_x'))
        print(getattr(pt, 'x'))
        print(getattr(pt, 'unknow', False))

        // Вывод
        1
        10
        False

акже при момощи этого метода можно получать не только значение 
переменной обьекта, но и переменной класса.

     print('Point.x = ', getattr(Point, 'x'))
     
     // Вывод 
     Point.x = 10

### Метод hasattr(obj, name)
Метод проверяет существует ли переменная в обьекте вабще, и 
возвращает True/False.

    class Point():
        x = 10
        y = 20

        def __init__(self):
            self.dinamic_x = 1
            self.dinamic_y = 2

    pt = Point()

    print("Существует ли pt.dinamic_x = ", hasattr(pt, 'dinamic_x'))
    print("Существует ли pt.x = ", hasattr(pt, 'x'))

    print("Существует ли Point.dinamic_x = ", hasattr(Point, 'dinamic_x'))
    print("Существует ли Point.x = ", hasattr(Point, 'x'))


    // Вывод
    Существует ли pt.dinamic_x =  True
    Существует ли pt.x =  True
    Существует ли Point.dinamic_x =  False
    Существует ли Point.x =  True

Как можно видеть из примера, функция проверяет не как обьект так и 
класс на существование некой переемнной, как статической так и
динамической.

### Метод setattr(obj, name, value)
Устанавливает переменную если ее не существовало ранее, и дает новое 
значение старой переменной.

    class MyClass:
        x = 10
        y = 20

        def __init__(self, name, my_list):
            self.name = name
            self.my_list = my_list

    m = MyClass('Название', [1, 2, 3])

    print(m.__dict__)
    setattr(m, 'new_var', 55)
    setattr(m, 'name', 'Новое название')
    print(m.__dict__)

    print(MyClass.__dict__)
    setattr(MyClass, 'new_static_var', 777)
    print(MyClass.__dict__)

На этом примере можно увидеть что данный метод позволяет не только 
создавать новые переменные обьекта так и изменять старые, также 
его можно использовать чтобы создавать новые статические переменные
или заменять их.

### Метод delattr(obj, name)
Удаляет атрибут что обьекта что класса.

    delattr(m, 'name')

### Атрибут класса/обьекта/модуля __dict__
`__dict__` метод возвращает словарь который будет седержать в себе
все переменные обьекта или класса.

        class Point():
            x = 10
            y = 20
            def __init__(self):
                self.dinamic_x = 1
                self.dinamic_y = 2

        pt = Point()
        print(pt.__dict__)

        // Вывод
        {'dinamic_x': 1, 'dinamic_y': 2}

Используется для получения не только переменных обьекта, но и всей
кучи имен зарегестрированных в модуле.

Также можно использовать для получения таблицы символов класса а не 
только обьекта.

        class Point():
            x = 10
            y = 20
            def __init__(self):
                self.dinamic_x = 1
                self.dinamic_y = 2

        print(Point.__dict__)

        // Вывод
        {
        '__module__': '__main__',
        'x': 10,
        'y': 20, 
        '__init__': <function func3.Point.__init__ at 0x7f76726e09d8>,
        '__dict__': <attribute '__dict__' of 'Point' objects>,
        '__weakref__': <attribute '__weakref__' of 'Point' objects>,
        '__doc__': None
        }

---


Проверка обьекта на True/False
---
---

В питоне обьект считается False только если он пустой, тоетсь
если мы делаем проверку в которой нас интересует есть ли в обьекте
хоть что-то, то можно сделать просто проверку как на условие `bool`

```python
    my_object = 'Test' # True example
    # my_object = '' # False example
    
    if len(my_object) > 0:
        print('my_object не пуст')
    
    if len(my_object):  # 0 преобразовывается к False
        print('my_object не пуст')
    
    if my_object != '':
        print('my_object не пуст')
    
    if my_object: # пустая строка преобразовывается к False
        print('my_object не пуст')

    # Вывод     
    # my_object не пуст
    # my_object не пуст
    # my_object не пуст
    # my_object не пуст
```