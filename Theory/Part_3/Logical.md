Логические операторы `and`, `or`, `not`
---
---

Если оба выражения с 2 сторон от оператора and верны, то 
выражение считается истинным.

```python
    if 7 > 1 and 5 > 3:
        print('ДА')
    else:
        print('НЕТ')

    a = 7 > 5 and 2 > 1
    print(a)

    # Вывод
    # ДА
    # True
```
---

Если оба выражения ложные, то только тогда все выражение
считается ложным, если хотя бы одно из них верное, то и все 
выражение считается истинным.

```python
    a = 7 > 7 or 2 > -1
    print(a)
    
    # Вывод
    # True
```

---

Оператор not инвертирует булево выражение, True становится
False, а False становится True.

```python
    if not False:
        print('да')
    else:
        print('нет')

    # Вывод
    # да
```



