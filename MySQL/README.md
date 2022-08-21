## MySQL.

### 명령어.

- 로그인: mysql -u username -p.
- 새로고침: FLUSH PRIVILEGES.
- 데이터베이스 확인: SHOW DATABASE.
- 데이터베이스 생성: CREATE DATABASE databasename (DEFAULT CHARACTER SET UTF8MB4).
- 데이터베이스 이동: USE databasename.
- 데이터베이스 삭제: DROP DATABASE databasename.
- 로컬 사용자 생성: CREATE USER ‘username’@’localhost’ identified by ‘password’.
- 외부 사용자 생성: CREATE USER ‘username’@’%’ identified by ‘password’.
- 로컬 사용자 삭제: DROP USER ‘username’@’localhost’.
- 외부 사용자 삭제: DROP USER ‘username’@’%’.
- 특정 사용자의 모든 권한 목록 확인: SHOW GRANTS FOR ‘username’@’localhost’.
- 특정 사용자에게 특정 데이터베이스의 모든 권한 부여: GRANT ALL ON databasename.* to ‘username’@’localhost’.
- 특정 사용자에게 특정 데이터베이스의 모든 권한 삭제: REVOKE ALL ON databasename.* from ‘username’@’localhost’.
- 테이블 생성: CREATE TABLE tablename(columnname datatype(int, varchar(16)), columnname datatype, …).
- 테이블 목록 확인: SHOW TABLES.
- 테이블 정보 확인: DESC tablename.
- 테이블 이름 변경: ALTER TABLE tablename RENAME newtablename.
- 테이블 컬럼 추가: ALTER TABLE tablename ADD COLUMN columnname datatype.
- 테이블 컬럼 변경(데이터 타입): ALTER TABLE tablename MODIFY COLUMN columnname datatype.
- 테이블 컬럼 변경(이름): ALTER TABLE tablename CHANGE COLUMN oldcolumnname newcolumnname newdatatype.
- 테이블 컬럼 삭제: ALTER TABLE tablename DROP COLUMN columnname.
- 테이블 삭제: DROP TABLE tablename.
- 데이터 추가: INSERT INTO tablename (column1, column2, …) VALUES (value1, value2, …).
- 데이터 조회: SELECT column1, column2, … FROM tablename.
- 데이터 조건: SELECT column1, column2, … FROM tablename WHERE condition.
- 데이터 수정: UPDATE tablename SET column1 = value1, column2 = value2, … WHERE condition.
- 데이터 삭제: DELETE FROM tablename WHERE condition.
- 데이터 정렬: SELECT column1, column2, … FROM tablename WHERE condition ORDER BY column1, column2, … ASC | DESC.
- 비교 연산자(A=B): SELECT column1, column2, … FROM tablename WHERE column1=value1.
- 비교 연산자(A>B): SELECT column1, column2, … FROM tablename WHERE column1>value1.
- 비교 연산자(A<B): SELECT column1, column2, … FROM tablename WHERE column1<value1.
- 비교 연산자(A≥B): SELECT column1, column2, … FROM tablename WHERE column1≥value1.
- 비교 연산자(A≤B): SELECT column1, column2, … FROM tablename WHERE column1≤value1.
- 비교 연산자(A<>B): SELECT column1, column2, … FROM tablename WHERE column1<>value1.
- 비교 연산자(A≠B): SELECT column1, column2, … FROM tablename WHERE column1≠value1.
- 논리 연산자(AND): SELECT column1, column2, … FROM tablename WHERE condition1 AND condition2 AND condition3 …
- 논리 연산자(OR): SELECT column1, column2, … FROM tablename WHERE condition1 OR condition2 OR (condition3 AND condition4) …
- 논리 연산자(NOT): SELECT column1, column2, … FROM tablename WHERE NOT condition.
- 논리 연산자(BETWEEN): SELECT column1, column2, … FROM tablename WHERE column1 BETWEEN value1 AND value2.
- 논리 연산자(IN): SELECT column1, column2, … FROM tablename WHERE column1 IN (value1, value2, …).
- 논리 연산자(LIKE): SELECT column1, column2, … FROM tablename WHERE column1 LIKE ‘%pattern’ | ‘pattern%’ | ‘%pattern%’ | ‘_attern’ | ‘__ttern%’.
- 쿼리 결과 합치기: SELECT column1, column2, … FROM tablename1 UNION | UNION ALL SELECT column1, column2, … FROM tablename2.
- JOIN(INNER): SELECT tablename1.column1, tablename1.column2, tablename2.column1, tablename2.column2 … FROM tablename1 INNER JOIN tablename2 ON tablename1.column1 = tablename2.column1 WHERE condition.
- JOIN(LEFT): SELECT tablename1.column1, tablename1.column2, tablename2.column1, tablename2.column2, … FROM tablename1(LEFT DATA TABLE) LEFT JOIN tablename2(RIGHT DATA TABLE) ON tablename1.column1 = tablename2.column1 WHERE condition.
- JOIN(RIGHT): SELECT tablename1.column1, tablename1.column2, tablename2.column1, tablename2.column2, … FROM tablename1(LEFT DATA TABLE) RIGHT JOIN tablename2(RIGHT DATA TABLE) ON tablename1.column1 = tablename2.column1 WHERE condition.
- JOIN(OUTER): SELECT tablename1.column1, tablename1.column2, tablename2.column1, tablename2.column2, … FROM tablename1(LEFT DATA TABLE) FULL OUTER JOIN tablename2(RIGHT DATA TABLE) ON tablename1.column1 = tablename2.column1 WHERE condition.
- JOIN(OUTER): SELECT column1, column2, … FROM tablename1 LEFT JOIN tablename2 ON tablename1.column1 = tablename2.column2 UNION SELECT column1, column2, … FROM tablename1 RIGHT JOIN tablename2 ON tablename1.column1 = tablename2.column2 WHERE condition.
- JOIN(SELF): SELECT column1, column2, … FROM tablename1, tablename2, … WHERE condition.
- 문자열 합치기: SELECT CONCAT (’string1’, ‘string2’) | SELECT CONCAT (’string1’, ‘string2’, column1 …) FROM tablename1.
- 별칭 생성: SELECT column1 AS alias FROM tablename1 | SELECT column1, column2, … FROM tablename1 AS alias.
- 쿼리 결과 중복 제외: SELECT DISTINCT column1, column2 FROM tablename1.
- 쿼리 결과 제한 조회: SELECT column1, column2, … FROM tablename WHERE condition LIMIT number.

### 용어.

- DB(Database)는 데이터의 집합체를 말한다.
- DBMS(Database Management System)는 데이터베이스를 관리할 수 있게 하는 시스템을 말한다.
- RDB(Relational Database)는 관계형 데이터베이스를 의미하고 데이터 간에 서로 관계가 있는 데이터 테이블을 모아둔 데이터 저장공간을 말한다.
- SQL(Structured Query Language)는 데이터베이스에서 데이터를 정의·조작·제작하기 위해 사용하는 언어를 말한다.

### 정보.

- SQL(Structured Query Language)는 1) 데이터 정의 언어, 2) 데이터 조작 언어, 3) 데이터 제어 언어로 구성되어 있다.
    - 데이터 정의 언어(DDL, Data Definition Language)는 데이터베이스 혹은 데이터 테이블을 생성·변경·삭제할 수 있는 명령어다. (예: CREATE, ALTER, DROP)
    - 데이터 조작 언어(DML, Data Manipulation Language)는 데이터베이스 혹은 데이터 테이블에 실제 데이터를 삽입·변경·삭제·조회할 수 있는 명령어다. (예: INSERT, UPDATE, DELETE, SELECT)
    - 데이터 제어 언어(DCL, Data Control Language)는 계정 별 권한을 설정해 주거나 실행 단위를 묶어서 실행이 실패했을 경우 롤백할 수 있는 명령어다. (예: GRANT, REVOKE, COMMIT, ROLLBACK)
- 사용자 정보는 ‘mysql’ 데이터베이스에서 관리하고 있다. 그러므로 사용자 정보를 조회하기 위해서는 ‘mysql’ 데이터베이스로 이동하고 조회하여야 한다.
    - USE databasename;
    - SELECT host, user FROM user;
- 키(Key)는 데이터베이스에서 조건에 만족하는 튜플을 찾거나 순서대로 정렬할 때 다른 튜플들과 구별할 수 있는 유일한 기준이 되는 속성이다.
- 조인은 두 개의 데이터 테이블을 결합하는 방법을 말한다.
    - Inner Join: 두 개의 데이터 테이블에서 공통 영역의 데이터를 가져오는 방법이다.
        - 공통 영역 밖의 데이터는 조회되지 않는다.
    - Full Outer Join: 두 개 데이터 테이블에서 공통 영역을 포함하여 다른 데이터 테이블을 모두 포함하는 방법이다.
    - Left Join: 두 개의 데이터 테이블에서 공통 영역을 포함하여 왼쪽 데이터 테이블의 데이터를 포함하는 방법이다.
        - 왼쪽 데이터 테이블의 데이터는 반드시 조회되고 공통된 영역의 데이터를 조회할 수 있다.
    - Right Join: 두 개의 데이터 테이블에서 공통 영역을 포함하여 오른쪽 데이터 테이블의 데이터를 포함하는 방법이다.
        - 오른쪽 데이터 테이블의 데이터는 반드시 조회되고 공통된 영역의 데이터를 조회할 수 있다.
