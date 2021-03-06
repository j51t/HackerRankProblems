# About this file
This file contains a series of HackerRank.com SQL problems and my corresponding solution. The problems are ordered by most recent completion

---
Write a query identifying the type of each record in the TRIANGLES table using its three side lengths. Output one of the following statements for each record in the table:

Equilateral: It's a triangle with  sides of equal length.
Isosceles: It's a triangle with  sides of equal length.
Scalene: It's a triangle with  sides of differing lengths.
Not A Triangle: The given values of A, B, and C don't form a triangle.
Input Format

The TRIANGLES table is described as follows:  
![TRIANGLES table](https://s3.amazonaws.com/hr-challenge-images/12887/1443815629-ac2a843fb7-1.png)


Solution:
```
SELECT 
CASE
    WHEN A + B <= C THEN "Not A Triangle"
    WHEN A = B AND B = C THEN "Equilateral"
    WHEN A = B OR B = C OR A = C THEN "Isosceles"
    ELSE "Scalene"
END
FROM TRIANGLES
```
---
Write a query that prints a list of employee names (i.e.: the name attribute) for employees in Employee having a salary greater than 2000 per month who have been employees for less than 10 months. Sort your result by ascending employee_id.

Input Format

The Employee table containing employee data for a company is described as follows:  
![EMPLOYEE table](https://s3.amazonaws.com/hr-challenge-images/19629/1458557872-4396838885-ScreenShot2016-03-21at4.27.13PM.png)

Solution:
```
SELECT NAME
FROM EMPLOYEE
WHERE
SALARY > 2000
AND
MONTHS < 10
ORDER BY EMPLOYEE_ID ASC
```
---
Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order.

Input Format

The Employee table containing employee data for a company is described as follows:  
![EMPLOYEE table](https://s3.amazonaws.com/hr-challenge-images/19629/1458557872-4396838885-ScreenShot2016-03-21at4.27.13PM.png)

Solution:
```
SELECT NAME
FROM EMPLOYEE
ORDER BY NAME ASC
```
-----------------------------------------------------------------------------------------------------------------------------------

Query the Name of any student in STUDENTS who scored higher than 75 Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.

Input Format  
![STUDENTS table](https://s3.amazonaws.com/hr-challenge-images/12896/1443815243-94b941f556-1.png)

Solution:
```
SELECT NAME 
FROM STUDENTS
WHERE MARKS > 75
ORDER BY RIGHT(NAME,3), ID ASC
```
-----------------------------------------------------------------------------------------------------------------------------------
Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.

Input Format

The STATION table is described as follows:  
![STATION table](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

Solution:
```
SELECT DISTINCT CITY
FROM STATION
WHERE
LOWER(LEFT(CITY,1)) NOT IN ('a','e','i','o','u')
AND
LOWER(RIGHT(CITY,1)) NOT IN ('a','e','i','o','u')
```
-----------------------------------------------------------------------------------------------------------------------------------
Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.

Input Format

The STATION table is described as follows:  
![STATION table](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

Solution:
```
SELECT DISTINCT CITY
FROM STATION
WHERE
LOWER(LEFT(CITY,1)) NOT IN ('a','e','i','o','u')
OR
LOWER(RIGHT(CITY,1)) NOT IN ('a','e','i','o','u')
```
-----------------------------------------------------------------------------------------------------------------------------------
Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates.

Input Format

The STATION table is described as follows  
![STATION table](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

Solution:
```
SELECT DISTINCT CITY
FROM STATION
WHERE LOWER(RIGHT(CITY,1)) NOT IN ('a','e','i','o','u')
```
-----------------------------------------------------------------------------------------------------------------------------------
Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.

Input Format

The STATION table is described as follows:  
![STATION table](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

Solution:
```
SELECT DISTINCT CITY
FROM STATION
WHERE LOWER(LEFT(CITY,1)) NOT IN ('a','e','i','o','u')
```
-----------------------------------------------------------------------------------------------------------------------------------
Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.

Input Format

The STATION table is described as follows:  
![STATION table](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

Solution:
```
SELECT DISTINCT CITY
FROM STATION
WHERE 
LOWER(LEFT(CITY,1)) IN ('a','e','i','o','u')
AND
LOWER(RIGHT(CITY,1)) IN ('a','e','i','o','u')
```


-----------------------------------------------------------------------------------------------------------------------------------
Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.

Input Format

The STATION table is described as follows:  

![STATION table](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

Solution:
```
SELECT DISTINCT CITY
FROM STATION
WHERE LOWER(RIGHT(CITY,1))
IN ('a','e','i','o','u')
```
-----------------------------------------------------------------------------------------------------------------------------------
Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. Your result cannot contain duplicates.

Input Format

The STATION table is described as follows:  

![STATION table](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

solution:
```
SELECT DISTINCT CITY
FROM STATION
WHERE LOWER(LEFT(CITY,1)) 
IN ('a','e','i','o','u')
```
-----------------------------------------------------------------------------------------------------------------------------------
Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.
The STATION table is described as follows:  

![STATION table](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

Solution
```
SELECT CITY, LENGTH(CITY)
FROM STATION
ORDER BY LENGTH(CITY), CITY ASC
LIMIT 1;

SELECT CITY, LENGTH(CITY)
FROM STATION
ORDER BY LENGTH(CITY) DESC
LIMIT 1;
```
-----------------------------------------------------------------------------------------------------------------------------------
Find the difference between the total number of CITY entries in the table and the number of distinct CITY entries in the table.
The STATION table is described as follows:  

![STATION table](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

solution
```
SELECT COUNT(CITY) - COUNT(DISTINCT CITY)
FROM STATION;
```

-----------------------------------------------------------------------------------------------------------------------------------
Query a list of CITY names from STATION for cities that have an even ID number. Print the results in any order, but exclude duplicates from the answer.
The STATION table is described as follows:  
![STATION table](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

Solution
```
SELECT DISTINCT CITY
FROM STATION
WHERE ID % 2 = 0;
```
-----------------------------------------------------------------------------------------------------------------------------------
Query a list of CITY and STATE from the STATION table.
The STATION table is described as follows:  
[STATION table]
![STATION table](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

Solution:
```
SELECT CITY, STATE
FROM STATION
```

-----------------------------------------------------------------------------------------------------------------------------------
Query the names of all the Japanese cities in the CITY table. The COUNTRYCODE for Japan is JPN.
The CITY table is described as follows:  
![CITY table](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

Solution:
```
SELECT NAME
FROM CITY
WHERE COUNTRYCODE = "JPN";
```
-----------------------------------------------------------------------------------------------------------------------------------
Query all attributes of every Japanese city in the CITY table. The COUNTRYCODE for Japan is JPN.

The CITY table is described as follows:  

![CITY table](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

Solution:
```
SELECT *
FROM CITY
WHERE COUNTRYCODE = "JPN";
```

-----------------------------------------------------------------------------------------------------------------------------------
Query all columns for a city in CITY with the ID 1661.

The CITY table is described as follows:  

https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg

Solution:
```
SELECT *
FROM CITY
WHERE ID = 1661
```

-----------------------------------------------------------------------------------------------------------------------------------
Query all columns (attributes) for every row in the CITY table.

The CITY table is described as follows:  

![CITY table](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

Solution:
```
select *
from city;
```
-----------------------------------------------------------------------------------------------------------------------------------
Query the NAME field for all American cities in the CITY table with populations larger than 120000. The CountryCode for America is USA.

The CITY table is described as follows:  

![CITY table](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

SOLUTION:
```
SELECT NAME
FROM CITY
WHERE POPULATION > 120000
AND COUNTRYCODE = "USA";
```
-----------------------------------------------------------------------------------------------------------------------------------
Query all columns for all American cities in the CITY table with populations larger than 100000. The CountryCode for America is USA.

The CITY table is described as follows:  

![CITY table](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

SOLUTION:
```
SELECT * 
from CITY 
where POPULATION > 100000 
and COUNTRYCODE = "USA";
```
