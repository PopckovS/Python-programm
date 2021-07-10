Сбор мусора - garbage collection
---
---

Существует 2 способа сборки мусора и питон использует их оба одновременно.

1) reference counting - первый способ подсчет ссылок, когда количество 
ссылок на обьект падает до нуля, этот обьект удаляется из памяти, это удобно 
и происходит сразу как количество ссылок доходит до нуля,  имеет и 
недостатки.
   
Во первых количество ссылок на обьект надо где то хранить что занимает память.

Во вторых присвоение или удаление происходит при каждой оперрации, тоесть 
занимает время выполнения программы.

В третьих сборщик мусора ну учитывает цциклические ссылки, которые всегда 
ссылаются др на др и удалить их не представляется возможным, ибо количество
ссылок никогдаа не упадет до нуля.

**Циклические ссылки**
Циклическую ссылку нельзя создать при помощи 2 обьектов, требуется минимум 3,
один как точка входа в цикл и 2 других как сам цикл:

```python
    class Cicle:
        
        def __init__(self, name):
            self.name = name

        def set_link(self, value):
            self.value = value

    main = Cicle('main')
    left = Cicle('left')
    right = Cicle('right')

    main.set_link('left')
    left.set_link('right')
    right.set_link('left')

    print(main.__dict__)
    print(left.__dict__)
    print(right.__dict__)

    # Вывод
    # {'name': 'main', 'value': 'left'}
    # {'name': 'left', 'value': 'right'}
    # {'name': 'right', 'value': 'left'}
```

Видим как два обьекта left и right ссылаются друг на друга, это и 
есть циклическая ссылка. Мы можем удалить внешние ссылки на сами обьекты но 
внутрении ссылки обьектов др на др останутся, они не удалятся но будут 
существовать и не будут доступны из вне ибо ссылки на внешний обьект уже 
пропал.

2) tracing - второй способ сбора мусора, суть его заключается в том что берется 
обьект и из него происходит проход по всем доступным ссылкам.
   
Если находятся обьекты которые не имеют доступ поссылкам из вне то они удаляются,
так и отслеживаются циклические ссылки.

**Еще пример циклических ссылок**
Имеем 2 списка, вносим один список в другой список, и вот получается кольцевая
ссылка, которую можно разрушить только в ручную, сам сборщик мусора ее не 
уберет.

```python
    # Пример циклич-х ссылок
    a = []
    b = []

    a.append(b)
    b.append(a)
```