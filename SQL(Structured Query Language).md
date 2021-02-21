# SQL(Structured Query Language)

# [1] SELECT

```sql
SELECT 컬럼1, 컬럼2, ...
FROM 테이블이름;
```

ex)

```sql
SELECT Country FROM Customers; //Customers테이블에서 Country컬럼만 출력

SELECT DISTINCT Country FROM Customers; //Customers테이블에서 Country만 출력(중복된 것은 지우고 출력)

SELECT COUNT(DISTINCT Country) FROM Customers; //Customers테이블에서 중복된것을 지운 Country의 갯수 출력
```



# [2] WHERE

```sql
SELECT 컬럼1, 컬럼2, ...
FROM 테이블이름
WHERE 조건
```



## - AND

## - OR

## -NOT



# [3] ORDER BY

```sql
SELECT 컬럼1, 컬럼2, ...
FROM 테이블이름
ORDER BY 컬럼1, 컬럼2, ... ASC|DESC;
```

ex)

```sql
SELECT * FROM Customers ORDER BY Country DESC; //Customers테이블에서 Country를 내림차순으로 출력

SELECT * FROM Customers ORDER BY Country, CustomerName; //Customers테이블에서 Country를 기준으로 오름차순정렬하고 Country가 같을시 CustomerName을 기준으로 오름차순 정렬

SELECT * FROM Customers ORDER BY Country ASC, CustomerName DESC; //Customers테이블에서 Country를 기준으로 오름차순정렬하고, COntry가 같을경우 CustomerName을 기준으로 내림차순 정렬한다.
```



# [4] INTO

```sql
INSERT INTO 테이블 (컬럼1,컬럼2,...)
VALUES(값1, 값2,...)
```



# [5] NULL

```sql
SELECT 컬럼
FROM 테이블
WHERE 컬럼 IS NULL;
//컬럼 값이 NULL값인 것을 찾아서 출력

SELECT 컬럼
FROM 테이블
WHERE 컬럼 IS NOT NULL;
//칼럼 값이 NULL이 아닌것을 찾아서 출려ㅑㄱ
```



# [6] UPDATE

```sql
UPDATE 테이블 
SET 컬럼1 = 값1, 컬럼2 = 값2
WHERE 조건;
```

ex)

```sql
UPDATE Customers
SET ContactName='Alfred Schmidt', City='Frankfurt'
WHERE CustomerId=1;
//Customers테이블에서 CustomerId가 1인 것을 ContactName은 Alfred Schmidt으로 City는 Frankfurt로 바꾸기

UPDATE Customers
SET ContactName='Juan';
//Customers에서 ContactName을 Juan으로 바꾼다.
```



# [7] DELETE

```sql
DELETE FROM 테이블 WHERE 조건;
```

ex)

```sql
DELETE FROM Customers WHERE CustomerName='Alfreds Futterkiste'
//Customers에서 CustomerName이 Alfreds Futterkiste것 삭제

DELETE FROM Customers
//Customers의 기록 삭제
```



# [8] MIN() and MAX()

* MIN : 조건에 맞는 테이블에서 가장작은 값의 칼럼을 출력

  ```sql
  SELECT MIN(칼럼)
  FROM 테이블
  WHERE 조건;
  ```

* MAX : 조건에 맞는 테이블에서 가장큰 값의 칼럼을 출력

  ```sql
  SELECT MAX(칼럼)
  FROM 테이블
  WHERE 조건;
  ```

ex)

```sql
SELECT MAX(Price) AS LargestPrice
FROM Products;
//Products에서 가장큰 Price값을 LargestPrice라는 이름으로 출력
```



# [9] COUNT(), AVG(), SUM()

* COUNT() : 조건에 맞는 row의 갯수
* AVG() : 컬럼의 평균 값 출력
* SUM() : 컬럼의 총합 출력

```sql
//COUNT()
SELECT COUNT(컬럼)
FROM 테이블
WHERE 조건;

//AVG()
SELECT AVG(컬럼)
FROM 테이블
WHERE 조건;

//SUM()
SELECT SUM(컬럼)
FROM 테이블
WHERE 조건;
```



# [10] LIKE

* % : 0개,1개 아니면 그 이상 갯수의 문자 의미
* _ : 문자1개 의미

```sql
SELECT 컬럼1, 컬럼2...
FROM 테이블
WHERE 컬럼 LIKE 패턴
```

ex)

```sql
WHERE CustomerName Like 'a%' //a로 시작하는 값 찾기

WHERE CustomerName Like '%a' //a로 끝나는 값 찾기

WHERE CustomerName Like '%or%' //or이 존재하는 값 찾기

WHERE CustomerName Like '_r%' //두번째 값이 r인 값 찾기

WHERE CustomerName Like 'a_%' //a가 적어도 뒤에서 세번째인 값 찾기

WHERE CustomerName Like 'a%o' //a로 시작하고 o으로 끝나는 값찾기

WHERE CustomerName NOT Like 'a%' //a로 시작하지 않는 값찾기 
```

# [11] Wildcards Characters

문자열에서 1개나 여러개의 문자를 구성하는 문자

| Symbol |               Description               |           Example            |
| :----: | :-------------------------------------: | :--------------------------: |
|   %    |          0개나 그 이상의 문자           | bl% => bl, black, blue, blob |
|   _    |                1개 문자                 |     h_t => hot, hat, hit     |
|  [ ]   |  [ ] 사이의 문자 중 아무거나 1개 가능   |      h[oa]t => hot, hat      |
|   ^    | [ ] 안에 있는 것 말고 다른 것들 중 하나 |     h[ ^oa]t => hit, ...     |
|   -    |              문자들의 범위              |     c[a-b]t => cat, cbt      |



# [12] IN

```sql
SELECT 컬럼
FROM 테이블
WHERE 컬럼 IN (값1, 값2...);
```

ex)

```sql
SELECT * FROM Customers
WHERE Country IN ('Germany','France','UK'); 
//Customers테이블에서 Country가 Germany나 France나 UK인 것을 찾음.

SELECT * FROM Customers
WHERE Country IN (SELECT Country FROM Suppliers);
//Suppliers테이블에 있는 Country의 값인 것을 찾음.
```



# [13] BETWEEN

```sql
SELECT 컬럼 
FROM 테이블
WHERE 컬럼 BETWEEN 값1 AND 값2;
```

ex)

```sql
SELECT * FROM Product WHERE Price BETWEEN 10 AND 20;
//Price가 10과 20사이인 값 찾기

SELECT * FROM Products WHERE ProductName BETWEEN 'Carnarvon Tigers' AND 'Mozzarella di Giovanni' ORDER BY ProductName;

SELECT * FROM Orders WHERE OrderDate BETWEEN '1996-07-01' AND '1996-07-31'
//두 날짜 사이인 값 찾기
```



# [14] Aliases(AS)

별명을 붙여줌

```sql
SELECT CustomerName, CONCAT(Address,', ',PostalCode,', ',City,', ',Country) AS Address FROM Customers;
//Address, PostalCode, City, Country 형식을 Address라는 이름으로 해서 CustomerName과 Address두개를 보여줌

SELECT o.OrderID, o.OrderDate, c.CustomerName
FROM Customers AS c, Orders AS o
WHERE c.CustomerName="Around the Horn" AND c.CustomerID=o.CustomerID;
```



# [15] JOIN

* INNER JOIN : 양쪽 테이블에서 두개의 값이 매칭되는 경우만 반환
* LEFT(OUTER) JOIN : 왼쪾테이블 전체 값과 매칭되는 오른쪽 테이블 값을 반환
* RIGHT (OUTER) JOIN : 오른쪽 테이블 전체 값과 매칭되는 왼쪽테이블 값을 반환
* FULL (OUTER) JOIN : 양쪽 테이블 모든 것의 값을 반환

## - INNER JOIN

```sql
SELECT 컬럼
FROM 테이블1
INNER JOIN 테이블2
ON 테이블1.컬럼명 = 테이블2.컬럼명;
```

ex)

```sql
SELECT Orders.OrderId, Customers.CustomerName 
FROM Orders
INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID;

SELECT
FROM ((Orders
INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID)
INNER JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID);
```



## - LEFT JOIN

## - RIGHT JOIN

## - FULL OUTER JOIN

## - Self JOIN

# [16] UNION



# [17] GROUP BY



# [18] HAVING



# [19] EXISTS



# [20] ANY, ALL



# [21] SELECT INTO



# [22] INSERT INTO SELECT



# [23]CASE



# [24] LIMIT

* LIMIT 1 : 맨 위에서부터 1개까지의 정보 조회
* LIMIT 3 : 맨 위에서부터 3개까지의 정보 조회
* LIMIT 2,6 :  위에서 2번쨰부터 6번째까지의 정보 조회

```sql
SELECT 컬럼
FROM 테이블
WHERE 조건
LIMIT 1;
//테이블에서 조건인 컬럼값중 맨위의 정보 하나만 반환
```

