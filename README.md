Python-programm
---

Сборник теории и решения практических упражнений по python-3.8.

[Ссылки на полезный материал.](links.md)

[Вопросики.](questions.md)

---

Теория :
---
 
1.  **Часть №1. Основное :**

    - [Основы Python](Theory/Part_1/Base.md )
    - [Разница версий и строки Unicod](Theory/Part_1/Version_difference.md )
    - [Области видимости LEGB](Theory/Part_1/Scopes_LEGB.md)
    - [Память в Си и память в Pyhton](Theory/Part_1/Memory_C_Python.md)
    - [Механизм управления памятью Pymalloc](Theory/Part_1/Memory_Pymalloc.md )
    - [Сборщик мусора](Theory/Part_1/Garbage_collector.md )
    - [Интерактивный режим REPL](Theory/Part_1/Interactive_mode_REPL.md )
    - [Аннотации методов аргументов](Theory/Part_1/Annotations.md )


2. **Часть №2. Типы данных в Python :**

    - [Типы данных](Theory/Part_2/Data_types.md)
    - [Boolean](Theory/Part_2/Boolean.md)
    - [Int и Float](Theory/Part_2/Integer_float.md)
    - [String](Theory/Part_2/String.md)
    - [None](Theory/Part_2/None.md)
    - [Списки - list](Theory/Part_2/List.md)
    - [Словарь - dict](Theory/Part_2/Dict.md)
    - [Множества - set, frozenset](Theory/Part_2/set.md )
    - [Кортеж - tuple](Theory/Part_2/Tuple.md)


3. **Часть №3. Операторы :**
    - [Арифметические операторы](Theory/Part_3/Arithmetic.md) (`+`, `-`, `*`, `/`, `//`, `%`, `**`)
    - [Побитовые Операторы](Theory/Part_3/Bitwise.md) (`&`, `|`, `^`, `>>`, `<<`, `~`)
    - [Операторы присваивания](Theory/Part_3/Assigment.md) (`=`, `+=`, `-=`, `/=`, `//=`)
    - [Оператор сравнения](Theory/Part_3/Comparison.md) (`==`, `!=`, `>`, `<`, `>=`, `<=`)
    - [Логические операторы](Theory/Part_3/Logical.md) (`and`, `or`, `not`)
    - [Операторы тождественности](Theory/Part_3/Identity.md) (`is`, `is not`)
    - [Операторы принадлежности](Theory/Part_3/Membership.md) (`in`, `not in`)


4. **Часть №4. Потоки управления :**
   
    - [Условие](Theory/Part_4/If_else.md) (`if`, `elif`, `else`)
    - [Тернарный оператор](Theory/Part_4/Ternary_operator.md )
    - [Цикл `for`](Theory/Part_4/For.md) ( и функция `range()` )
    - [Цикл `while`](Theory/Part_4/While.md)
    - [Блок `try` и `except`, `else`, `finally`](Theory/Part_4/Try.md)
    - [Прерывание `break`](Theory/Part_4/Break.md)
    - [Прерывание `continue`](Theory/Part_4/Continue.md)

   
5. **Часть №5. Функции :**

    - [Функции](Theory/Part_5/Functions.md)
    - [Замыкания функций](Theory/Part_5/Function_closures.md)
    - [Функции - lambda](Theory/Part_5/Function_lambda.md)
    - [Аргументы функции упаковка / распаковка](Theory/Part_5/Packing_and_unpacking_function_arguments.md)
    - [Аргументы функции по умолчанию](Theory/Part_5/Default_function_arguments.md)
    - [Методы range и xrange](Theory/Part_5/Method_range_xrange.md)


6. **Часть №6. Обьекты :**

    - [Обьекты 1](Theory/Part_6/Object_1.md )
    - [Обьекты 2](Theory/Part_6/Object_2.md )
    - [Обьекты - функторы, @classmethod и @staticmethod, абстрактный метод, перегрузка ](Theory/Part_6/Object_3.md )
    - [Дескрипторы обьектов](Theory/Part_6/Descriptors.md )
    - [Модификаторы доступа public, protected, private](Theory/Part_6/Access_modifiers.md)
    - [Приватности в обьектах](Theory/Part_6/Privacy.md)
    - [Атрибут __slots__](Theory/Part_6/Mechanism__slots__.md )
    - [Наследование обьектов](Theory/Part_6/Inheritance.md )
    - [Магические методы ( dunder )](Theory/Part_6/Dunder_method.md )
    - [Паттерны программирования](Theory/Part_6/Pattern.md )
   

7. **Часть №7. Разное - 1 :**

    - [Итераторы и Выражения-генераторы ](Theory/Part_7/Iterators_expression_generators.md)
    - [Функции-генераторы yield](Theory/Part_7/Yield.md)
    - [Генерация списков](Theory/Part_7/List_comprehensions.md)
    - [Исключения - Exception](Theory/Part_7/Exceptions.md)
    - [Менеджеры контекста with](Theory/Part_7/With.md)
    - [Декораторы методов и классов](Theory/Part_7/Decorator.md)
    - [Функции all() any() ](Theory/Part_7/Function_all_any.md)
   

8. **Часть №8 Разное - 2 :**

    - [Файлы Ввод/Вывод](Theory/Part_8/File.md)
    - [Получение информации о памяти обьекта __sizeof__() и sys.getsizeof()](Theory/Part_8/Get_information_about_memory.md )
    - [Копирование copy() и deepcopy()](Theory/Part_8/Copy_object.md )
    - [Ellipsis ...](Theory/Part_8/Ellipsis.md)
    - [Особая распаковка (не функции)](Theory/Part_8/Unpacking.md)
    - [Функция enumerate](Theory/Part_8/Function_enumerate.md)
    - [Функции globals() locals() vars()](Theory/Part_8/Scopes_functions.md)
    - [Хэширование hash()](Theory/Part_8/Hash.md)
   

9. **Часть №9. Модули :**
   
    - [Модуль os и shutil ](Theory/Part_9/Module_os.md)
    - [Модуль sys](Theory/Part_9/Module_sys.md)
    - [Модуль functools](Theory/Part_9/Module_functools.md)
    - [Модуль weakref](Theory/Part_9/Module_weakref.md)
    - [Модуль re - регулярные выражения](Theory/Part_9/Module_re.md)
    - [Модуль random](Theory/Part_9/Module_random.md)
    - [Модуль time](Theory/Part_9/Module_time.md)
    - [Модуль Async](Theory/Part_9/Module_Async.md)
    - [Модуль crontab](Theory/Part_9/Module_crontab.md)


10. **Часть №10. Интересные вопросы по Python :**

    - [Вопросы 1](Theory/Part_10/Questions_1.md)
    - [Вопросы 2](Theory/Part_10/Questions_2.md)
   
11. **Часть №11. Модули :**
   
    - [Модуль numpy](Theory/Part_11/Module_numpy.md)  
    - [Модуль matplotlib](Theory/Part_11/Module_matplotlib.md)

---

Практика :
---

1) **[Часть №1 :](Example/)**

    1 [](Example/Practice_1/)
    2 [](Example/Practice_1/)
    3 [](Example/Practice_1/)
   


