Цикл `while`
---
---
В то время как `for` итерируется по последовательности ровно 
столько, сколько есть элементов в последовательности, в то время 
как цикл `while` работает до тех пор, пока верно некое условие.

Мы можем итерироваться по возрастанию и по убыванию.
```python
    iter = 10
    while iter >= 0:
        print(iter)
        iter -= 1
        
    iter = 0
    while iter <= 10:
        print(iter)
        iter += 1

    # Вывод
    # 10 9 8 7 6 5 4 3 2 1 0
    # 0 1 2 3 4 5 6 7 8 9 10
```
