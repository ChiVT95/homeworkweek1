```sql=
###Revising the Select Query II

SELECT NAME FROM CITY WHERE COUNTRYCODE="USA" AND POPULATION>120000;

###Select All

SELECT * FROM CITY;

###Select By ID

SELECT * FROM CITY WHERE ID=1661;

###Japanese Cities' Attributes

SELECT *
FROM CITY
WHERE COUNTRYCODE="JPN";

###Japanese Cities' Names

SELECT NAME
FROM CITY
WHERE COUNTRYCODE="JPN";

###Weather Observation Station 1

SELECT CITY,STATE FROM STATION;

###Weather Observation Station 3

SELECT distinct CITY
FROM STATION
WHERE (ID%2)=0;

###Weather Observation Station 4

SELECT (COUNT(CITY)-COUNT(distinct CITY)) 
FROM STATION;

###Weather Observation Station 5

select top 1 city, len(city) from station order by len(city), city; 
select top 1 city, len(city) from station order by len(city) desc, city desc;

###Weather Observation Station 6

select distinct city from station where substring(city, 1, 1) in ('a', 'e', 'i', 'o', 'u');

###Weather Observation Station 7

SELECT DISTINCT CITY FROM STATION WHERE RIGHT(CITY,1) IN ('a','i','e','o','u');

###Weather Observation Station 8

select distinct city from station 
where left(city,1) in ('a','e','i','o','u') 
and right(city, 1) in ('a','e','i','o','u');

###Weather Observation Station 9

SELECT DISTINCT(CITY) FROM STATION WHERE LEFT(CITY,1) NOT IN ('A','E','I','O','U');

###Weather Observation Station 11

SELECT DISTINCT CITY FROM STATION WHERE LEFT(CITY, 1) NOT IN ('A', 'E', 'I', 'O', 'U') OR RIGHT(CITY, 1) NOT IN ('a', 'e', 'i', 'o', 'u');

###Weather Observation Station 12

SELECT distinct CITY FROM STATION WHERE CITY LIKE "[^aeiouAEIOU]%[^aeiouAEIOU]";

###Higher Than 75 Marks

SELECT NAME FROM STUDENTS WHERE MARKS > 75 ORDER BY RIGHT(NAME, 3), ID ASC;

###Employee Names

SELECT NAME 
FROM EMPLOYEE
ORDER BY NAME;

###Employee Salaries

SELECT name FROM Employee
WHERE salary > 2000 AND months < 10
ORDER BY employee_id;

###Type of Triangle

SELECT CASE             
            WHEN A + B > C AND B + C > A AND A + C > B THEN
                CASE 
                    WHEN A = B AND B = C THEN 'Equilateral'
                    WHEN A = B OR B = C OR A = C THEN 'Isosceles'
                    ELSE 'Scalene'
                END
            ELSE 'Not A Triangle'
        END
FROM TRIANGLES;

###Revising Aggregations - The Count Function

select count(*)
    from CITY
        where Population > 100000;

###Revising Aggregations - The Sum Function

SELECT SUM(POPULATION) FROM CITY WHERE DISTRICT = "CALIFORNIA";

###Revising Aggregations - Averages

SELECT AVG(population)
FROM city
WHERE district = 'California';

###Average Population

SELECT FLOOR(AVG(POPULATION)) FROM CITY;

###Japan Population

select sum(population) from city where countrycode='JPN';

###Population Density Difference

SELECT MAX(population) - MIN(population)
FROM city;

###Weather Observation Station 2

select format(sum(lat_n) , '.##'), format(sum(long_w) , '.##') from station;

###Weather Observation Station 10

select distinct city from station where city regexp "[^'aeiou']$";

###Weather Observation Station 13

select CAST(SUM(LAT_N) as Decimal(12,4)) from Station where LAT_N between 38.7880 and 137.2345;

###Weather Observation Station 14

select CAST(MAX(LAT_N) AS DECIMAL (10,4)) from station
where LAT_N < 137.2345;

###Weather Observation Station 15

SELECT ROUND(LONG_W,4)
FROM STATION
WHERE LAT_N = (SELECT MAX(LAT_N) FROM STATION WHERE LAT_N < 137.2345);


###Weather Observation Station 16

select top 1 cast(LAT_N as decimal(10,4)) from STATION where LAT_N > 38.7780 order by LAT_N asc;

###Weather Observation Station 17

select cast(long_w as decimal(20,4)) from station where lat_n = (select min(lat_n) from station where lat_n > 38.7780);

###Asian Population

SELECT SUM(CITY.POPULATION)
FROM CITY
INNER JOIN COUNTRY ON CITY.COUNTRYCODE = COUNTRY.CODE 
WHERE COUNTRY.CONTINENT = 'Asia';

###African Cities

SELECT
    city.name
FROM
    city
    JOIN country
    ON city.countrycode = country.code
WHERE continent = 'Africa';

###Top Earners

select (salary * months)as earnings ,count(*) from employee group by 1 order by earnings desc limit 1;

###The Blunder

SELECT CEIL(AVG(Salary)-AVG(REPLACE(Salary,'0',''))) FROM EMPLOYEES;

###Average Population of Each Continent

SELECT COUNTRY.CONTINENT, FLOOR(AVG(CITY.POPULATION))
FROM CITY INNER JOIN COUNTRY
ON CITY.COUNTRYCODE = COUNTRY.CODE
GROUP BY COUNTRY.CONTINENT;

###Draw The Triangle 1

DECLARE @i INT = 20
WHILE (@i > 0) 
BEGIN
   PRINT REPLICATE('* ', @i) 
   SET @i = @i - 1
END

###Draw The Triangle 2

DECLARE @var smallint = 1;

WHILE @var < 21 BEGIN SELECT REPLICATE('* ', @var); SET @var += 1; END;

```


