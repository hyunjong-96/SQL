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

# [10] LIKE



# [11] Wildcards Characters



# [12] IN



# [13] BETWEEN



# [14] Aliases(AS)



# [15] JOIN



# [16] UNION



# [17] GROUP BY



# [18] HAVING



# [19] EXISTS



# [20] ANY, ALL



# [21] SELECT INTO



# [22] INSERT INTO SELECT



# [23]CASE