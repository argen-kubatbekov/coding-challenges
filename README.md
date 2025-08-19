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
### **Task 5 (5kyu)**

[Ссылка на задачу](https://www.codewars.com/kata/5868b2de442e3fb2bb000119/train/python)

**Описание:**
*** Closest and Smallest ***
Input
a string strng of n positive numbers (n = 0 or n >= 2)
Let us call weight of a number the sum of its digits. For example 99 will have "weight" 18, 100 will have "weight" 1.

Two numbers are "close" if the difference of their weights is small.

Task:
For each number in strng calculate its "weight" and then find two numbers of strng that have:

the smallest difference of weights ie that are the closest
with the smallest weights
and with the smallest indices (or ranks, numbered from 0) in strng
Output:
an array of two arrays, each subarray in the following format:
[number-weight, index in strng of the corresponding number, original corresponding number in strng]

or a pair of two subarrays (Haskell, Clojure, FSharp) or an array of tuples (Elixir, C++)

or a (char*) in C or a string in some other languages mimicking an array of two subarrays or a string

or a matrix in R (2 rows, 3 columns, no columns names)

The two subarrays are sorted in ascending order by their number weights if these weights are different, by their indexes in the string if they have the same weights.

Examples:
Let us call that function closest

strng = "103 123 4444 99 2000"
the weights are 4, 6, 16, 18, 2 (ie 2, 4, 6, 16, 18)

closest should return [[2, 4, 2000], [4, 0, 103]] (or ([2, 4, 2000], [4, 0, 103])
or [{2, 4, 2000}, {4, 0, 103}] or ... depending on the language)
because 2000 and 103 have for weight 2 and 4, their indexes in strng are 4 and 0.
The smallest difference is 2.
4 (for 103) and 6 (for 123) have a difference of 2 too but they are not 
the smallest ones with a difference of 2 between their weights.
....................

strng = "80 71 62 53"
All the weights are 8.
closest should return [[8, 0, 80], [8, 1, 71]]
71 and 62 have also:
- the smallest weights (which is 8 for all)
- the smallest difference of weights (which is 0 for all pairs)
- but not the smallest indices in strng.
....................

strng = "444 2000 445 544"
the weights are 12, 2, 13, 13 (ie 2, 12, 13, 13)

closest should return [[13, 2, 445], [13, 3, 544]] or ([13, 2, 445], [13, 3, 544])
or [{13, 2, 445}, {13, 3, 544}] or ...
444 and 2000 have the smallest weights (12 and 2) but not the smallest difference of weights;
they are not the closest.
Here the smallest difference is 0 and in the result the indexes are in ascending order.
...................

closest("444 2000 445 644 2001 1002") --> [[3, 4, 2001], [3, 5, 1002]] or ([3, 4, 2001], 
[3, 5, 1002]]) or [{3, 4, 2001}, {3, 5, 1002}] or ...
Here the smallest difference is 0 and in the result the indexes are in ascending order.
...................

closest("239382 162 254765 182 485944 468751 49780 108 54")
The weights are: 27, 9, 29, 11, 34, 31, 28, 9, 9.
closest should return  [[9, 1, 162], [9, 7, 108]] or ([9, 1, 162], [9, 7, 108]) 
or [{9, 1, 162}, {9, 7, 108}] or ...
108 and 54 have the smallest difference of weights too, they also have 
the smallest weights but they don't have the smallest ranks in the original string.
..................

closest("54 239382 162 254765 182 485944 468751 49780 108")
closest should return  [[9, 0, 54], [9, 2, 162]] or ([9, 0, 54], [9, 2, 162])
or [{9, 0, 54}, {9, 2, 162}] or ...
Notes :
If n == 0 closest("") should return []

or ([], []) in Haskell, Clojure, FSharp

or [{}, {}] in Elixir or '(() ()) in Racket

or {{0,0,0}, {0,0,0}} in C++

or "[(), ()]" in Go, Nim,

or "{{0,0,0}, {0,0,0}}" in C, NULL in R

or "" in Perl.

See Example tests for the format of the results in your language.




**Решение:**
```python
def closest(strng):
    mass = [sum(int(x) for x in i) for i in strng.split()]
    if len(mass) < 2:
        return []
    str_lst = [int(x) for x in strng.split()]
    
    indx = [i for i in range(len(mass))]
    
    z = [list(i) for i in zip(mass, indx, str_lst)]
    
    z.sort(key=lambda x: (x[0], x[1], x[2]))
    
    pairs = []

    for i in range(len(z) - 1):
        a = z[i]
        b = z[i + 1]
        diff = abs(a[0] - b[0])
        pairs.append([diff, a, b])
    
    min_p = min(pairs, key=lambda x: (x[0], x[1]))
    min_p.pop(0)
    return min_p

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














