# 📊 Week 1 Report — Python + SQL

 Python
**Task 1 Python Codewards** - 6 kyu: Are they the "same"?

Description:
Given two arrays a and b write a function comp(a, b) (orcompSame(a, b)) that checks whether the two arrays have the "same" elements, with the same multiplicities (the multiplicity of a member is the number of times it appears). "Same" means, here, that the elements in b are the elements in a squared, regardless of the order.

Examples
Valid arrays
a = [121, 144, 19, 161, 19, 144, 19, 11]  
b = [121, 14641, 20736, 361, 25921, 361, 20736, 361]
comp(a, b) returns true because in b 121 is the square of 11, 14641 is the square of 121, 20736 the square of 144, 361 the square of 19, 25921 the square of 161, and so on. It gets obvious if we write b's elements in terms of squares:

a = [121, 144, 19, 161, 19, 144, 19, 11] 
b = [11*11, 121*121, 144*144, 19*19, 161*161, 19*19, 144*144, 19*19]
Invalid arrays
If, for example, we change the first number to something else, comp is not returning true anymore:

a = [121, 144, 19, 161, 19, 144, 19, 11]  
b = [132, 14641, 20736, 361, 25921, 361, 20736, 361]
comp(a,b) returns false because in b 132 is not the square of any number of a.

a = [121, 144, 19, 161, 19, 144, 19, 11]  
b = [121, 14641, 20736, 36100, 25921, 361, 20736, 361]
comp(a,b) returns false because in b 36100 is not the square of any number of a.

Remarks
a or b might be [] or {} (all languages except R, Shell).
a or b might be nil or null or None or nothing (except in C++, COBOL, Crystal, D, Dart, Elixir, Fortran, F#, Haskell, Nim, OCaml, Pascal, Perl, PowerShell, Prolog, PureScript, R, Racket, Rust, Shell, Swift).
If a or b are nil (or null or None, depending on the language), the problem doesn't make sense so return false.

**Solution:**  
def comp(array1, array2):
    if array1 is None or array2 is None:
        return False
    lst1 = sorted(i ** 2 for i in array1)
    lst2 = sorted(i for i in array2)
    return lst1 == lst2

----------------------------------------------------------------------------------------------------------------------------------------
**Task 2 Python Codewards** - 7 kyu: The highest profit wins!

Story
Ben has a very simple idea to make some profit: he buys something and sells it again. Of course, this wouldn't give him any profit at all if he was simply to buy and sell it at the same price. Instead, he's going to buy it for the lowest possible price and sell it at the highest.

Task
Write a function that returns both the minimum and maximum number of the given list/array.

Examples (Input --> Output)
[1,2,3,4,5] --> [1,5]
[2334454,5] --> [5,2334454]
[1]         --> [1,1]
Remarks
All arrays or lists will always have at least one element, so you don't need to check the length. Also, your function will always get an array or a list, you don't have to check for null, undefined or similar.

**Solution:** 
def min_max(lst):
    result = []
    result.append(min(lst))
    result.append(max(lst))
    return result

----------------------------------------------------------------------------------------------------------------------------------------
**Task 3 Python Codewards** - 8 kyu: Grasshopper - Grade book

Grade book
Complete the function so that it finds the average of the three scores passed to it and returns the letter value associated with that grade.

Numerical Score	Letter Grade
90 <= score <= 100	'A'
80 <= score < 90	'B'
70 <= score < 80	'C'
60 <= score < 70	'D'
0 <= score < 60	'F'
Tested values are all between 0 and 100. Theres is no need to check for negative values or values greater than 100.

**Solution:** 
def get_grade(s1, s2, s3):
    score = (s1 + s2 + s3) / 3
    if 90 <= score <= 100:
        return 'A'
    elif 80 <= score < 90:
        return 'B'
    elif 70 <= score < 80:
        return 'C'
    elif 60 <= score < 70:
        return 'D'
    else:
        return 'F'

----------------------------------------------------------------------------------------------------------------------------------------
**Task 4 Python Codewards** - 7 kyu: You are a Cube!

In geometry, a cube is a three-dimensional solid object bounded by six square faces, facets or sides, with three meeting at each vertex.The cube is the only regular hexahedron and is one of the five Platonic solids. It has 12 edges, 6 faces and 8 vertices.The cube is also a square parallelepiped, an equilateral cuboid and a right rhombohedron. It is a regular square prism in three orientations, and a trigonal trapezohedron in four orientations.

You are given a task of finding if the provided positive integer is a perfect cube -- a number that is the cube of an integer!

**Solution:** 
import math

def you_are_a_cube(cube):
    root = round(math.cbrt(cube))
    return cube == root ** 3

-----------------------------------------------------------------------------------------------------------------------------------------
**Task 5 Python Codewards** - 6 kyu: Find the unique number

There is an array with some numbers. All numbers are equal except for one. Try to find it!

find_uniq([ 1, 1, 1, 2, 1, 1 ]) == 2
find_uniq([ 0, 0, 0.55, 0, 0 ]) == 0.55
It’s guaranteed that array contains at least 3 numbers.

The tests contain some very huge arrays, so think about performance.

This is the first kata in series:

Find the unique number (this kata)
Find the unique string
Find The Unique

**Solution:** 
def find_uniq(arr):
    lst = [arr[0], arr[1], arr[2]]
    unique = list(i for i in lst if lst.count(i) == 1)
    s = list(set(arr))
    if not unique:
        s.append(arr[0])
        return next(i for i in s if s.count(i) == 1)
    else:
        return next(i for i in lst if lst.count(i) == 1)
----------------------------------------------------------------------------------------------------------------------------------------
sql-ex.ru
Рассматривается БД кораблей, участвовавших во второй мировой войне. Имеются следующие отношения:
Classes (class, type, country, numGuns, bore, displacement)
Ships (name, class, launched)
Battles (name, date)
Outcomes (ship, battle, result)
Корабли в «классах» построены по одному и тому же проекту, и классу присваивается либо имя первого корабля, построенного по данному проекту, либо названию класса дается имя проекта, которое не совпадает ни с одним из кораблей в БД. Корабль, давший название классу, называется головным.
Отношение Classes содержит имя класса, тип (bb для боевого (линейного) корабля или bc для боевого крейсера), страну, в которой построен корабль, число главных орудий, калибр орудий (диаметр ствола орудия в дюймах) и водоизмещение ( вес в тоннах). В отношении Ships записаны название корабля, имя его класса и год спуска на воду. В отношение Battles включены название и дата битвы, в которой участвовали корабли, а в отношении Outcomes – результат участия данного корабля в битве (потоплен-sunk, поврежден - damaged или невредим - OK).
Замечания. 1) В отношение Outcomes могут входить корабли, отсутствующие в отношении Ships. 2) Потопленный корабль в последующих битвах участия не принимает.
Задание: 

Найдите страны, имевшие когда-либо классы обычных боевых кораблей ('bb') и имевшие когда-либо классы крейсеров ('bc').

**Solution:** 
SELECT DISTINCT t1.country
FROM 
(SELECT DISTINCT c.country, s.name, o.ship
FROM Classes c
LEFT JOIN Ships s ON c.class = s.class
LEFT JOIN Outcomes o ON s.name = o.ship
WHERE type = 'bb') t1
JOIN 
(SELECT DISTINCT c.country, s.name, o.ship
FROM Classes c
LEFT JOIN Ships s ON c.class = s.class
LEFT JOIN Outcomes o ON s.name = o.ship
WHERE type = 'bc') t2
ON t1.country = t2.country
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Найдите корабли, `сохранившиеся для будущих сражений`; т.е. выведенные из строя в одной битве (damaged), они участвовали в другой, произошедшей позже.

**Solution:** 
SELECT DISTINCT t1.ship FROM
    (SELECT ship, date, result
    FROM Outcomes o
    JOIN Battles b ON o.battle = b.name
    WHERE result = 'damaged') t1
JOIN
    (SELECT ship, date, result
    FROM Outcomes o
    JOIN Battles b ON o.battle = b.name
    ) t2 
ON t1.ship = t2.ship AND t1.date < t2.date
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
