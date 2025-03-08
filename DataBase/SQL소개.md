# Introduction to SQL

---

## 1. Overview of the SQL Query Language 

<br>

- **역사와 발전**  
  - IBM의 System R 프로젝트에서 Sequel로 시작
  - ANSI/ISO 표준: SQL-86, SQL-89, SQL-92, SQL:1999, SQL:2003, SQL:2006, SQL:2008 등

<br>

- **SQL의 구성 요소**  
  - `**DDL:** 테이블, 스키마, 무결성 제약, 인덱스, 보안 및 물리적 저장구조 정의  
  - **DML:** 데이터 검색, 삽입, 삭제, 갱신  
  - **기타:** 트랜잭션 제어, 뷰 정의, 임베디드/동적 SQL, 권한 부여


<br>

## 2. SQL Data Definition

<br>

- **테이블 생성 및 스키마 정의**  
  - `CREATE TABLE` 명령으로 테이블 생성  
  - 각 속성은 자료형과 선택적 제약조건을 가짐  
  - 예시:
    ```sql
    create table department (
      dept_name varchar(20),
      building varchar(15),
      budget numeric(12,2),
      primary key (dept_name)
    );
    ```

- **기본 자료형**  
  - **문자열:** `char(n)` (고정 길이), `varchar(n)` (가변 길이), `nvarchar` (유니코드 지원)  
  - **숫자형:** `int`, `smallint`, `numeric(p,d)`, `real`, `double precision`, `float(n)`  
  - **NULL 값:** 존재하지만 값이 없음을 의미하며, 각 자료형은 NULL을 가질 수 있음

- **무결성 제약**  
  - **Primary Key:** 고유하며 NULL 불가  
  - **Foreign Key:** 다른 테이블의 기본키와 연계하여 참조 무결성 유지  
  - **Not Null:** 속성에 NULL 값이 들어가지 않도록 강제

<br>

## 3. Basic Structure of SQL Queries

<br>

### 단일 테이블

<br>

- 모든 부서의 이름을 출력한다면
  ```sql
  select dept_name
  from instructor;
  ```


- 중복 제거는 `DISTINCT` 사용
  ```sql
  select distinct dept_name
  from instructor;

  ```

<br>

### 다중 테이블

<br>

- **`SELECT` :** 출력할 속성 또는 표현식 지정
- **`FROM` :** 검색할 테이블(들)을 지정하며, 기본적으로 Cartesian product(데카르트 곱)를 생성
- **`WHERE` :** 튜플을 선택하기 위한 조건을 지정

<br>

- 여러 테이블의 데카르트 곱을 생성하므로, 반드시 `WHERE` 조건으로 원하는 튜플만 선택해야 함
```sql
select name, course_id
from instructor, teaches
where instructor.ID = teaches.ID;

```

<br>

### Natural Join

<br>

- 두 테이블 간 동일한 이름의 속성에 대해 자동으로 조인
- 아래 두 SQL문은 같은 결과를 출력한다

```sql
select name, course_id
from instructor natural join teaches;
```
```sql
select name, course_id
from instructor, teaches
where instructor.ID = teaches.ID;
```

<br>

### Join ... USING

<br>

- 특정 속성만으로 조인하도록 지정
- 아래 두 SQL문은 같은 결과를 출력한다

```sql
select name, title
from (instructor natural join teaches) join course using (course_id);
```
```sql
select name, title
from instructor natural join teaches, course
where teaches.course_id = course.course_id;
```

<br>

## 4. Additional Basic Operations

<br>

### Rename 또는 별칭 사용

<br>

- 속성 및 테이블 별칭: `AS` 를 사용하여 이름을 재정의

```sql
select T.name as instructor_name, S.course_id
from instructor as T, teaches as S
where T.ID = S.ID;

```

<br>

- SELF JOIN: 같은 테이블을 두 번 사용 시 별칭 필수

```sql
select distinct T.name
from instructor as T, instructor as S
where T.salary > S.salary and S.dept_name = 'Biology';

```

<br>

### 문자열 연산 및 패턴 매칭

<br>

- 문자열 표기: `'`로 감싸서 표현, 내부의 작은 따옴표라면 두 번 사용(`''`)
- 문자열 함수: `upper()`, `lower()`, `trim()` 등
- 패턴 매칭: `LIKE` 연산자와 `%` , `_` 등

```sql
select dept_name
from department
where building like '%Watson%';
```

<br>

- **이스케이프 문자:** 특수문자는 일반 문자로 인식하기 위해 `escape` 키워드 사용

<br>

`작성중입니다 .. .  쓸 게 굉장히 많네요 미친건가 .. . . . `
