# 📊 Week 2 Report — Python + SQL

---

## 🐍 Python — Codewars

### **Task 1 (7kyu)**
[Ссылка на задачу](https://www.codewars.com/kata/57cc4853fa9fc57a6a0002c2/train/python)

**Описание:**
*** No Loops Allowed ***

You will be given an array and a limit value, you must check that all values in the array are less than or equal to limit. If they all are, return true. Else, return false.

You can assume all values in the array are numbers.

Do not use loops. Do not modify input array.

**Решение:**
```python
def small_enough(a, limit): 
    return max(a, default=float('-inf')) <= limit
```
### **Task 2 (6kyu)**

[Ссылка на задачу](https://www.codewars.com/kata/54da5a58ea159efa38000836/train/python)

**Описание:**
*** Find the odd int ***

Given an array of integers, find the one that appears an odd number of times.
There will always be only one integer that appears an odd number of times.
Examples
[7] should return 7, because it occurs 1 time (which is odd).
[0] should return 0, because it occurs 1 time (which is odd).
[1,1,2] should return 2, because it occurs 1 time (which is odd).
[0,1,0,1,0] should return 0, because it occurs 3 times (which is odd).
[1,2,2,3,3,3,4,3,3,3,2,2,1] should return 4, because it appears 1 time (which is odd).

**Решение:**
```python
def find_it(seq):
    result = None
    for i in seq:
        if seq.count(i) % 2 != 0:
            result = i
    return result
```

### **Task 3 (6kyu)**

[Ссылка на задачу](https://www.codewars.com/kata/54da5a58ea159efa38000836/train/python)

**Описание:**
*** ----- ***


**Решение:**
```python

```
-----------------------------------------------------------------------------------------------------------------------------------------------------------

##  SQL

### **Task 1**

**Описание:**
*** БД Корабли ***

Укажите сражения, которые произошли в годы, не совпадающие ни с одним из годов спуска кораблей на воду.

**Решение:**

SELECT t.name
FROM 
    (SELECT name,
            EXTRACT(YEAR FROM date) as date
     FROM Battles) t
LEFT JOIN Ships s ON s.launched = t.date
WHERE s.launched IS NULL

### **Task 2** 
**Описание:**
*** БД Корабли ***

Найдите названия всех кораблей в базе данных, начинающихся с буквы R.

**Решение:**

SELECT name
FROM Ships
WHERE name LIKE 'R%'
UNION
SELECT ship
FROM Outcomes
WHERE ship LIKE 'R%'

### **Task 2** 
**Описание:**
*** БД Корабли ***

Найдите названия всех кораблей в базе данных, состоящие из трех и более слов (например, King George V).
Считать, что слова в названиях разделяются единичными пробелами, и нет концевых пробелов.

**Решение:**

SELECT name
FROM Ships
WHERE length(name) - length(replace(name, ' ', '')) >= 2
UNION
SELECT ship
FROM Outcomes
WHERE length(ship) - length(replace(ship, ' ', '')) >= 2















