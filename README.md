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

[Ссылка на задачу](https://www.codewars.com/kata/523f5d21c841566fde000009/train/python)

**Описание:**
*** Array.diff ***
Implement a function that computes the difference between two lists. The function should remove all occurrences of elements from the first list (a) that are present in the second list (b). The order of elements in the first list should be preserved in the result.

Examples
If a = [1, 2] and b = [1], the result should be [2].

If a = [1, 2, 2, 2, 3] and b = [2], the result should be [1, 3].


**Решение:**
```python
def array_diff(a, b):
    arr = set(a) - set(b)
    return [i for i in a + b if i in arr]
```

### **Task 4 (7kyu)**

[Ссылка на задачу](https://www.codewars.com/kata/539ee3b6757843632d00026b/train/python)

**Описание:**
*** Find the capitals ***
Write a function that takes a single non-empty string of only lowercase and uppercase ascii letters (word) as its argument, and returns an ordered list containing the indices of all capital (uppercase) letters in the string.

Example (Input --> Output)
"CodEWaRs" --> [0,3,4,6]


**Решение:**
```python
def capitals(word):
    return [i for i, ch in enumerate(word) if ch.isupper()]

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

### **Task 3** 
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

### **Task 4** 
**Описание:**
*** БД Корабли ***

Для каждого корабля, участвовавшего в сражении при Гвадалканале (Guadalcanal), вывести название, водоизмещение и число орудий.

**Решение:**

SELECT  o.ship as ship,
        c.displacement,
        c.numGuns
FROM Outcomes o
LEFT JOIN Ships s ON o.ship = s.name
LEFT JOIN Classes c ON c.class = COALESCE(s.class, o.ship)
WHERE o.battle = 'Guadalcanal'

### **Task 5** 
**Описание:**
*** БД Корабли ***

Определить страны, которые потеряли в сражениях все свои корабли.

**Решение:**

WITH all_ships AS (
    SELECT country, name
    FROM Classes c
    JOIN Ships s ON c.class = s.class
    UNION
    SELECT country, ship
    FROM Classes c
    JOIN Outcomes o ON c.class = o.ship
    )

SELECT DISTINCT country
FROM all_ships
WHERE country NOT IN (SELECT country
                      FROM all_ships
                      WHERE name NOT IN (SELECT ship
                                         FROM Outcomes
                                         WHERE result = 'sunk')
                      )














