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
- 로그인: mysql -h <endpoint> -p <port> -u <username> -p.
- 파일 실행: source </path/filename.sql>.
- 파일 실행: mysql -u username -p databasename < </path/filename.sql>
- 특정 데이터베이스 백업(LOCAL): mysqldump -u username -p databasename > backup.sql.
- 특정 데이터베이스 백업(AWS RDS): mysqldump —set-gtid-purged=OFF -h <hostname> -p <port> -u <username> -p <databasename> > <filename.sql>.
- 모든 데이터베이스 백업: mysqldump -u username -p —all-databases > backup.sql.
- 테이블 백업: mysqldump -u username -p databasename tablename > backup.sql.
- 특정 테이블 스키마 백업: mysqldump -d -u username -p databasename tablename > backup.sql.
- 모든 테이블 스키마 백업: mysqldump -d -u username -p databasename > backup.sql.
- 기본키 생성: CREATE TABLE tablename(column1 datatype, column2 datatype, … CONSTRAINT constraintname PRIMARY KEY (column1, column2, …)).
- 기본키 생성: ALTER TABLE tablename ADD PRIMARY KEY (column1, column2, …).
- 기본키 삭제: ALTER TABLE tablename DROP PRIMARY KEY.
- 외래키 생성: CREATE TABLE tablename(column1 datatype, column2 datatype, column3 datatype, column4 datatype, … CONSTRAINT constraintname PRIMARY KEY (column1, column2, …), CONSTRAINT constraintname FOREIGN KEY (column3, column4, …) REFERENCES REF_tablename(REF_column).
- 외래키 생성: ALTER TABLE tablename ADD FOREIGN KEY (column) REFERENCES REF_tablename(REF_column).
- 외래키 삭제: ALTER TABLE tablename DROP FOREIGN KEY FK_constraint.
- 키 정보 확인: SHOW CREATE TABLE tablename

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
    - USE mysql.
    - SELECT host, user FROM user.
- 키(Key)는 데이터베이스에서 조건에 만족하는 튜플을 찾거나 순서대로 정렬할 때 다른 튜플들과 구별할 수 있는 유일한 기준이 되는 속성이다.
- 조인은 두 개의 데이터 테이블을 결합하는 방법을 말한다.
    - Inner Join: 두 개의 데이터 테이블에서 공통 영역의 데이터를 가져오는 방법이다.
        - 공통 영역 밖의 데이터는 조회되지 않는다.
    - Full Outer Join: 두 개 데이터 테이블에서 공통 영역을 포함하여 다른 데이터 테이블을 모두 포함하는 방법이다.
    - Left Join: 두 개의 데이터 테이블에서 공통 영역을 포함하여 왼쪽 데이터 테이블의 데이터를 포함하는 방법이다.
        - 왼쪽 데이터 테이블의 데이터는 반드시 조회되고 공통된 영역의 데이터를 조회할 수 있다.
    - Right Join: 두 개의 데이터 테이블에서 공통 영역을 포함하여 오른쪽 데이터 테이블의 데이터를 포함하는 방법이다.
        - 오른쪽 데이터 테이블의 데이터는 반드시 조회되고 공통된 영역의 데이터를 조회할 수 있다.
- AWS RDS(Amazon Relational Database Service)는 클라우드에서 간편하게 데이터베이스를 설치, 운영 및 확장할 수 있는 관리형 서비스 모음이다.
- AWS RDS(Amazon Relational Database Service)에 접속하기 위해 데이터베이스의 엔드포인트 및 포트 정보가 필요하다.
- SQL(Structured Query Language)은 파일 안에 여러 개의 쿼리를 작성하고 저장할 수 있다. 그리고 이 파일을 실행하면 작성되어 있는 모든 쿼리를 동시에 실행할 수 있다.
- SQL(Structured Query Language)은 파일 안에 여러 개의 쿼리를 작성하여 데이터베이스를 백업·복원할 수 있다. 그리고 이 때에는 파일의 경로를 확인하여 실행하여야 한다.
- 테이블에는 일반적으로 테이블의 각 행을 고유하게 식별하는 값을 가진 열 또는 열 조합이 포함되어 있습니다. 이러한 열이나 열 조합은 테이블의 PK(기본 키)라고 하며 테이블에 엔터티 무결성을 적용합니다. 기본 키 제약 조건은 데이터의 고유성을 보장하므로 자주 ID 열에 정의됩니다.
- 외래 키(FK)는 두 테이블의 데이터 간 연결을 설정하고 강제 적용하여 외래 키 테이블에 저장될 수 있는 데이터를 제어하는 데 사용되는 열입니다. 외래 키 참조에서는 한 테이블의 기본 키 값을 가지고 있는 열을 다른 테이블의 열이 참조할 때 두 테이블 간에 연결이 생성됩니다. 이때 두 번째 테이블에 추가되는 열이 외래 키가 됩니다.

## MySQL with Python.

### 코드.

```
1. 로그인. 
mydb = mysql.connector.connect(
    host = "<hostname>",
    port = "<port>",
    user = "<username>",
    password = "<password>",
    database = "<databasename>"
)

mydb.close()

2. 쿼리.
mydb = mysql.connector.connect(
    host = "<hostname>",
    port = "<port>",
    user = "<username>",
    password = "<password>",
    database = "<databasename>"
)

mycursor = mydb.cursor()
mycursor.execute(<"query">)

mydb.close()

3. 파일: 단일 쿼리.
mydb = mysql.connector.connect(
    host = "<hostname>",
    port = "<port>",
    user = "<username>",
    password = "<password>",
    database = "<databasename>"
)

sql = open("<filename.sql>").read()

mycursor = mydb.cursor()
mycursor.execute(sql)

mydb.close()

4. 파일: 다수 쿼리.
mydb = mysql.connector.connect(
    host = "<hostname>",
    port = "<port>",
    user = "<username>",
    password = "<password>",
    database = "<databasename>"
)

sql = open("<filename.sql>").read()

mycursor = mydb.cursor()
result = mycursor.execute(sql, multi=True)
for result_iterator in result:
	if result_iterator.with_rows:
		print(result_iterator.fetchall())
	else:
		print(result_iterator.statement)

mydb.commit()
mydb.close()

5. 데이터 저장.
mydb = mysql.connector.connect(
    host = "<hostname>",
    port = "<port>",
    user = "<username>",
    password = "<password>",
    database = "<databasename>"
)

dataframe = pd.read_csv("filename.csv", encoding='euc-kr')

sql = """INSERT INTO <"databasename"> VALUES (%s, %s, %s, ...)"""
mycursor = mydb.cursor(buffered=True)
for i, row in dataframe.iterrows():
	mycursor.execute(sql, tuple(row))
	mydb.commit()

mydb.close()**

```

## MySQL, Inflearn.
- 전체 행의 개수(결측값 포함): SELECT COUNT(*) FROM tablename.
- 전체 행의 개수(결측값 제외): SELECT COUNT(columnname) FROM tablename.
- 전체 행의 개수(결측값 및 중복값 제외): SELECT COUNT(DISTINCT columnname) FROM tablename.
- 전체 행의 합계: SELECT SUM(columname) FROM tablename.
- 전체 행의 평균(결측값 제외): SELECT AVG(columname) FROM tablename.
- 전체 행의 평균(결측값 포함): SELECT SUM(columname)/COUNT(*) FROM tablename.
- 전체 행의 최소: SELECT MIN(columnname) FROM tablename.
- 전체 행의 최대: SELECT MAX(columnname) FROM tablename.
- 그룹 데이터: SELECT columnname1, columnname2, … FROM tablename GROUP BY columnname1, columnname2, … HAVING condition1, condition2, ….
- SELECT CASE WHEN columnname = value AND|OR columnname = value, … THEN value, WHEN columnname = value AND|OR columnname = value, … THEN value ELSE value END FROM tablename.
