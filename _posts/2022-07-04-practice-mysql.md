---   
layout: post  
title: "[MySQL] MySQL 기본 정리"
date: 2022-07-04
excerpt: "이 포스트는 MySQL 기본 문법을 정리한 내용입니다."
tag:
- mysql
comments: true
---  
🔗[강의는 이수안컴퓨터연구소 유튜브 MySQL 강의를 참고하였습니다.](https://www.youtube.com/watch?v=vgIc4ctNFbc&list=PLAsbL2NvnmK7HZ4wyxdFkvqMTtu6Mr9gY&index=5&ab_channel=%EC%9D%B4%EC%88%98%EC%95%88%EC%BB%B4%ED%93%A8%ED%84%B0%EC%97%B0%EA%B5%AC%EC%86%8C)

# 현재 서버에 어떤 DB가 있는지 보기
SHOW DATABASE

# USE
- 사용할 데이터베이스 지정
- 지정해 놓은 후 특별히 다시 USE문 사용하거나 다른 DB를 사용하겠다고 명시하지 않는 이상 모든 SQL문은 지정 DB에서 수행
USE database_name
- workbench에서 직접 선택해 사용가능
- [Navigator] -> [SCHEMAS] -> 데이터베이스 선택

# SHOW TABLE
- 데이터베이스 world의 테이블 이름 보기

# SHOW TABLE STATUS
- 데이터베이스 world의 테이블 정보 조회

# DESCRIBE (DESC)
- city 테이블에 무슨 열이 있는지 확인
- DESCRIBE table_name;
- DESC city; 

# SELECT ... FROM
- 요구하는 데이터를 가져오는 구문
- 일반적으로 가장 많이 사용되는 구문
- 데이터베이스 내 테이블에서 원하는 정보를 추출
- SELECT의 구문형식
SELECT select_expr
	[FROM table_references]
	[WHERE where_condition]
	[GROUP BY {col_name | expr | position}]
	[HAVING where_condition]
	[ORDER BY {col_name | expr | position}]

# SELECT 열 이름
- 테이블에서 필요로 하는 열만 가져오기
- 여러 개의 열을 가져오고 싶을 때는 콤마로 구분
- 열 이름의 순서는 출력하고 싶은 순서대로 배열

# SELECT FROM WHERE
- 기본적인 WHERE절
- 조회하는 결과에 특정한 조건으로 원하는 데이터만 보고싶을때
- SELECT 필드이름 FROM 테이블 이름 WHERE 조건식;
- 조건이 없을 경우 테이블의 크기가 클수록 찾는 시간과 노력이 증가

# 관계 연산자
- OR
- AND
- 조건 (=, <>, != 등)
- 관계연산자(NOT, AND, OR 등)

# BETWEEN
- 데이터가 숫자로 구성되어 있어 연속적인 값은 BETWEEN ... AND 사용 가능

# IN
- 이산적인 값의 조건에는 IN() 사용 가능
SELECT *
FROM city
WHERE NAME IN('SEOUL', 'NEW YORK', 'TOKYO');

# LIKE
- 문자열 내용 검색 위해 LIKE 연산자 사용
- 문자 뒤에 % - 무엇이든(%) 허용
- 한 글자와 매치하기 위해서는 '_' 사용
SELECT *
FROM city
WHERE NAME IN('SEOUL', 'NEW YORK', 'TOKYO');

# Sub Query
- 쿼리 문 안에 또 쿼리문 들어 있는 것
- 서브 쿼리의 결과가 둘 이상이 되면 에러 발생
SELECT *
FROM city
WHERE CountryCode = (SELECT CountryCode
			FROM city
			WHERE Name = 'Seoul');

# 예제. 한국과 미국에 있는 도시들 보기, 단 한국에 있는 도시들 중에 인구가 1000000 이상인 도시 보기
SELECT *
FROM city
WHERE (CountryCode = "KOR" AND Population >= 1000000) OR CountryCode = "USA";
# ANY
- 서브쿼리의 여러 개 결과 중 한 가지만 만족해도 가능
- SOME은 ANY와 동일한 의미로 사용
- =ANY 구문은 IN과 동일한 의미 

# ALL
- 서브쿼리의 여러 개 결과를 모두 만족시켜야 함

# ORDER BY
- 결과가 출력되는 순서를 조절
- 기본적으로 오름차순 정렬 : ASC(오름차순) -> 생략가능
- 내림차순으로 정렬은 열 이름 뒤에 DESC
- ORDER BY 구문 혼합 가능

# DISTINCT
- 중복된 것은 1개씩만 보여주면서 출력
- 테이블의 크기가 클수록 효율적
SELECT DISTINCT CountryCode
FROM city;

# LIMIT
- 출력 개수를 제한
- 상위 N개만 출력하는 'LIMIT N'구문
- 서버의 처리량을 많이 사용해 서버의 전반적인 성능을 나쁘게 하는 악성 쿼리문 개선할 때 사용
SELECT *
FROM city
ORDER BY Population DESC
LIMIT 10

# GROUP BY
- 그룹으로 묶어주는 역할
- 집계함수 함께 사용
AVG(), MIN(), MAX(), COUNT() : 행 개수, COUNT(DISTINCT) : 중복 제외 행 개수,
STDEV(), VARIANCE()
- 효율적인 데이터 그룹화
- 읽기 좋게 하기 위해 별칭 사용
SELECT CountryCode, Max(Population) AS 'Population'
FROM city
GROUP BY CountryCode

# 예제. 도시는 몇개인가?
SELECT COUNT(NAME) AS NUM 
from city

# 예제. 도시들의 평균 인구수는?
SELECT AVG(Population)
FROM city

# HAVING
- WHERE과 비슷한 개념으로 조건 제한
- 집계 함수에 대해서 조건 제한하는 편리한 개념
- HAVING절은 반드시 GROUP BY절 다음에 나와야 함

# ROLLUP
- 총합 또는 중간합계가 필요한 경우 사용
- GROUP BY절과 함께 WITH ROLLUP문 사용
SELECT CountryCode, Name, SUM(Population)
FROM city
GROUP BY CountryCode , Name WITH ROLLUP

# JOIN
- 데이터베이스 내의 여러 테이블에서 가져온 레코드를 조합하여 하나의 테이블이나 결과 집합으로 표현
SELECT *
FROM city
JOIN country ON city.CountryCode = country.Code

# 예제. city, country, countrylanguage 테이블 3개를 JOIN 하기
SELECT *
FROM city
JOIN country ON city.CountryCode = country.Code
JOIN countrylanguage ON city.CountryCode = countrylanguage.CountryCode

# MySQL 내장함수
- 사용자의 편의를 위해 다양한 기능의 내장 함수를 미리 정의하여 제공
- 대표적인 내장함수 종류 : 문자열 함수, 수학 함수, 날짜와 시간 함수

# LENGTH()
- 전달받은 문자열의 길이를 반환

# CONCAT()
- 전달받은 문자열을 결합하여 하나의 문자열로 반환
- 전달받은 문자열 중 하나라도 NULL이 존재하면 NULL 반환

# LOCATE()
- 문자열 내에서 찾는 문자열이 처음으로 나타나는 위치를 찾아서 해당 위치 반환
- 찾는 문자열이 문자열 내에 존재하지 않는다면 0 반환
- MYSQL에서는 문자열의 시작 인덱스를 1부터 계산
SELECT LOCATE('abc', 'abababababABCDabcAB')

# LEFT(), RIGHT()
- LEFT() : 문자열의 왼쪽부터 지정한 개수만큼의 문자 반환
- RIGHT() : 문자열의 오른쪽부터 지정한 개수만큼의 문자 반환
SELECT 
LEFT('MYSQL is an open source relational database management system.', 5),
RIGHT('MYSQL is an open source relational database management system.', 5);

# LOWER(), UPPER()
- LOWER() : 문자열의 문자를 모두 소문자로 변경
- UPPER() : 문자열의 문자를 모두 대문자로 변경
SELECT 
LOWER('MYSQL is an open source relational database management system.'),
UPPER('MYSQL is an open source relational database management system.');

# REPLACE()
- 문자열에서 특정 문자열을 대체, 문자열로 교체
SELECT REPLACE('MSSQL', 'MS', 'My') # 결과 : MSSQL -> MySQL

# TRIM()
- 문자열의 앞이나 뒤, 또는 양쪽 모두에 있는 특정 문자 제거
- TRIM() 함수에서 사용할 수 있는 지정자
BOTH : 전달받은 문자열의 양 끝에 존재하는 특정 문자 제거(기본설정)
LEADING : 전달받은 문자열 앞에 존재하는 특정 문자 제거
TRAILING : 전달받은 문자열 뒤에 존재하는 특정 문자 제거
- 만약 지정자를 명시하지 않으면, 자동으로 BOTH로 설정
- 제거할 문자를 명시하지 않으면, 자동으로 공백 제거
SELECT TRIM('                MYSQL           '), -> MYSQL
TRIM(LEADING '#' FROM '###MYSQL##'), -> MYSQL##
TRIM(TRAILING '#' FROM '###MYSQL##'); -> ###MYSQL

# FORMAT()
- 숫자타입의 데이터를 세 자리마다 쉼표(,)를 사용하는 '#,###,###.##' 형식으로 변환
- 반환되는 데이터 형식은 문자열 타입
- 두번째 인수는 반올림할 소수 부분의 자릿수
SELECT FORMAT(123123123.123123,3);

# FLOOR() : 내림, CEIL() : 올림, ROUND():반올림

# SQRT() : 양의 제곱근, POW() : 첫 번째 인수로는 밑수를 전달하고, 두번째 인수로는 지수롤 전달하여 거듭제곱 계산
# EXP() : 인수로 지수를 전달받아, e의 거듭제곱 계산, LOG() : 자연로그 값 계산

# SIN(), COS(), TAN()

# ABS(), RAND()
- ABS() : 절댓값 반환
- RAND() : 0.0보다 크거나 같고 1.0보다 작은 하나의 실수를 무작위로 생성

# NOW() : 현재 날짜와 시간을 반환, 반환되는 값은 'YYYY-MM-DD HH:MM:SS' 또는 YYYYMMDD 형태로 반환

# CURDATE() : 현재 날짜 반환, 이때 반환되는 값은 'YYYY-MM-DD' 또는 YYYYMMDD 형태로 반환

# CURTIME() : 현재 시각 반환, 이때 반환되는 값은 'HH:MM:SS' 또는 HHMMSS 형태로 반환

# DATE() : 전달받은 값에 해당하는 날짜 정보 반환
# MONTH() :월에 해당하는 값 반환, 0부터 12사이의 값 가짐
# DAY() : 일에 해당하는 값 반환, 0부터 31 사이의 값 가짐
# HOUR() : 시간에 해당하는 값 반환, 0부터 23 사이의 값 가짐
# MINUTE() : 분에 해당하는 값 반환, 0부터 59 사이의 값 가짐
# SECOND() : 초에 해당하는 값 반환, 0부터 59 사이의 값 가짐

# MONTHNAME() : 월에 해당하는 이름 반환
# DAYNAME() : 요일에 해당하는 이름 반환

# DAYOFWEEK() : 일자가 해당 주에서 몇번째 날인지를 반환, 1부터 7 사이의 값 반환 (일요일=1, 토요일=7)
# DAYOFMONTH() : 일자가 해당 월에서 몇번째 날인지를 반환, 0부터 31 사이의 값 반환
# DAYOFYEAR() : 일자가 해당 연도에서 몇 번째 날인지를 반환, 1부터 366 사이의 값 반환

# DATE_FORMAT() : 전달받은 형식에 맞춰 날짜와 시간 정보를 문자열로 반환
SELECT
DATE_FORMAT(NOW(), '%D %y %a %d %m %n %j')

# CREATE TABLE AS SELECT
- city 테이블과 똑같은 city2 테이블 생성
CREATE TABLE city2 AS SELECT * FROM city;

# CREATE DATABASE
- 새로운 데이터베이스 생성
- USE 문으로 새 데이터베이스 사용
CREATE DATABASE chohu;
USE chohu;

# CRATE TABLE 새로 생성
CREATE TABLE test2 (
	id INT NOT NULL PRIMARY KEY,
    col1 INT NULL,
    col2 FLOAT NULL
    col3 VARCHAR(45) NULL
)

# ALTER TABLE
- ALTER TABLE 문과 함께 ADD 문을 사용하면, 테이블에 컬럼을 추가할 수 있음
ALTER TABLE test2
ADD col3 VARCHAR(45) NULL,
ADD col4 INT NULL;
- ALTER TABLE 문과 함께 MODIFY 문을 사용하면, 테이블의 컬럼 타입을 변경할 수 있음









