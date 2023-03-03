# Base-de-datos-JOINS
 ## 1. Show the name of the towns and its country name. Sort the results sorted by country name and town name. Make four versions:
Using an explicit inner join,
using an implicit inner join,
using a left outer join,
and using a right outer join.
explicit inner join
implicit inner join

###### EXPLICIT INNER JOIN VERSION:

~~~
SELECT T.NAME, C.NAME
FROM TOWNS T
INNER JOIN COUNTRIES C
ON T.COUNTRY = C.ID
ORDER BY C.NAME ASC, T.NAME;
~~~

| name | name |
| :--- | :--- |
| Palma de Mallorca | Spain |
| Liverpool | United Kingdom |
| London | United Kingdom |
| Manchester | United Kingdom |

###### IMPLICIT INNER JOIN VERSION:

~~~
SELECT T.NAME, C.NAME
FROM TOWNS T, COUNTRIES C
WHERE T.COUNTRY = C.ID
ORDER BY C.NAME ASC, T.NAME;
~~~

| name | name |
| :--- | :--- |
| Palma de Mallorca | Spain |
| Liverpool | United Kingdom |
| London | United Kingdom |
| Manchester | United Kingdom |

###### LEFT OUTER JOIN VERSION:

~~~
SELECT T.NAME, C.NAME
FROM TOWNS T
LEFT OUTER JOIN COUNTRIES C
ON T.COUNTRY = C.ID
ORDER BY C.NAME ASC, T.NAME;
~~~

| name | name |
| :--- | :--- |
| Palma de Mallorca | Spain |
| Liverpool | United Kingdom |
| London | United Kingdom |
| Manchester | United Kingdom |
| Athens | null |

###### RIGHT OUTER JOIN VERSION:

~~~
SELECT T.NAME, C.NAME
FROM TOWNS T
RIGHT OUTER JOIN COUNTRIES C
ON T.COUNTRY = C.ID
ORDER BY C.NAME ASC, T.NAME;
~~~

| name | name |
| :--- | :--- |
| null | Italy |
| Palma de Mallorca | Spain |
| Liverpool | United Kingdom |
| London | United Kingdom |
| Manchester | United Kingdom |

## 2. Show the name of the teams with the town name and country name. Sort the results sorted by name of town and name of team. Make five versions:
Using an explicit inner join,
using an implicit inner join,
using a left outer join,
using a right outer join,
using a full outer join.

###### EXPLICIT INNER JOIN VERSION:

~~~
SELECT T.NAME, O.NAME, C.NAME
FROM TEAMS T
INNER JOIN TOWNS O
   ON  T.TOWN = O.ID
INNER JOIN  COUNTRIES C
   ON O.COUNTRY = C.ID
ORDER BY O.NAME, T.NAME;
~~~

| name | name | name |
| :--- | :--- | :--- |
| Liverpool | Liverpool | United Kingdom |
| Arsenal | London | United Kingdom |
| Chelsea | London | United Kingdom |
| Tottenham Hotspur | London | United Kingdom |
| Manchester City | Manchester | United Kingdom |
| Manchester United | Manchester | United Kingdom |
| R. C. D. Mallorca | Palma de Mallorca | Spain |

###### IMPLICIT INNER JOIN VERSION:

~~~
SELECT T.NAME, O.NAME, C.NAME
FROM TEAMS T , TOWNS O , COUNTRIES C
WHERE O.COUNTRY = C.ID AND T.TOWN = O.ID
ORDER BY O.NAME, T.NAME;
~~~

| name | name | name |
| :--- | :--- | :--- |
| Liverpool | Liverpool | United Kingdom |
| Arsenal | London | United Kingdom |
| Chelsea | London | United Kingdom |
| Tottenham Hotspur | London | United Kingdom |
| Manchester City | Manchester | United Kingdom |
| Manchester United | Manchester | United Kingdom |
| R. C. D. Mallorca | Palma de Mallorca | Spain |

###### LEFT OUTER JOIN VERSION:

~~~
SELECT T.NAME, O.NAME, C.NAME
FROM TEAMS T
LEFT OUTER JOIN TOWNS O
   ON  T.TOWN = O.ID
LEFT OUTER JOIN  COUNTRIES C
   ON O.COUNTRY = C.ID
ORDER BY O.NAME, T.NAME;
~~~

| name | name | name |
| :--- | :--- | :--- |
| Liverpool | Liverpool | United Kingdom |
| Arsenal | London | United Kingdom |
| Chelsea | London | United Kingdom |
| Tottenham Hotspur | London | United Kingdom |
| Manchester City | Manchester | United Kingdom |
| Manchester United | Manchester | United Kingdom |
| R. C. D. Mallorca | Palma de Mallorca | Spain |
| C. D. Amigos | null | null |

###### RIGHT OUTER JOIN VERSION:

~~~
SELECT T.NAME, O.NAME, C.NAME
FROM TEAMS T
RIGHT OUTER JOIN TOWNS O
   ON  T.TOWN = O.ID
RIGHT OUTER JOIN  COUNTRIES C
   ON O.COUNTRY = C.ID
ORDER BY O.NAME, T.NAME;
~~~

| name | name | name |
| :--- | :--- | :--- |
| Liverpool | Liverpool | United Kingdom |
| Arsenal | London | United Kingdom |
| Chelsea | London | United Kingdom |
| Tottenham Hotspur | London | United Kingdom |
| Manchester City | Manchester | United Kingdom |
| Manchester United | Manchester | United Kingdom |
| R. C. D. Mallorca | Palma de Mallorca | Spain |
| null | null | Italy |

###### FULL OUTER JOIN VERSION:

~~~
SELECT T.NAME, O.NAME, C.NAME
FROM TEAMS T
FULL OUTER JOIN TOWNS O
   ON  T.TOWN = O.ID
FULL OUTER JOIN  COUNTRIES C
   ON O.COUNTRY = C.ID
ORDER BY O.NAME, T.NAME;
~~~

| name | name | name |
| :--- | :--- | :--- |
| null | Athens | null |
| Liverpool | Liverpool | United Kingdom |
| Arsenal | London | United Kingdom |
| Chelsea | London | United Kingdom |
| Tottenham Hotspur | London | United Kingdom |
| Manchester City | Manchester | United Kingdom |
| Manchester United | Manchester | United Kingdom |
| R. C. D. Mallorca | Palma de Mallorca | Spain |
| C. D. Amigos | null | null |
| null | null | Italy |

## 3. Select the name of the towns and the numbers of teams of the town. Sort the results by town name. Make two versions:
Using an explicit inner join,
using a left outer join.
explicit inner join
left outer join

###### EXPLICIT INNER JOIN VERSION:
  
~~~
SELECT O.NAME, COUNT(T.NAME)
FROM TEAMS T
INNER JOIN TOWNS O
   ON  T.TOWN = O.ID
GROUP BY O.NAME
ORDER BY O.NAME;
~~~

| name | count |
| :--- | :--- |
| Liverpool | 1 |
| London | 3 |
| Manchester | 2 |
| Palma de Mallorca | 1 |

###### LEFT OUTER JOIN VERSION:
 
~~~
SELECT O.NAME, COUNT(T.NAME)
FROM TEAMS T
RIGHT OUTER JOIN TOWNS O
   ON  T.TOWN = O.ID
GROUP BY O.NAME
ORDER BY O.NAME;
~~~

| name | count |
| :--- | :--- |
| Athens | 0 |
| Liverpool | 1 |
| London | 3 |
| Manchester | 2 |
| Palma de Mallorca | 1 |

## 4. Show the name of the towns that don't have teams using a left outer join.

###### LEFT OUTER JOIN :

~~~
SELECT O.NAME
FROM TOWNS O
LEFT OUTER JOIN TEAMS T
ON  O.ID = T.TOWN
WHERE T.TOWN IS NULL ;
~~~

| name |
| :--- |
| Athens |

