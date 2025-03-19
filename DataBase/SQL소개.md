# Introduction to SQL

---

## 1. SQL 질의어의 개요 (Overview of the SQL Query Language)

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

## 2. SQL 데이터 정의 (SQL Data Definition)

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

## 3. SQL 질의의 기본 구조 (Basic Structure of SQL Queries)

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

## 4. 부가적인 기본 연산 (Additional Basic Operations)

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
- 패턴 매칭:
  - `Like` 연산자와 같이 사용
  - `%` : 임의의 문자열
  - `_` : 한 문자

```sql
select dept_name
from department
where building like '%Watson%';
```

<br>

- **이스케이프 문자:** `%`나 `_`등의 특수문자는 일반 문자로 인식하기 위해 `\` 키워드 사용
- `\`를 표현할 때는 `\\` 사용

```sql
select dept_name
from department
where building like '%Wat100\%son%';
```

<br>

### 전체 속성 선택 및 정렬

<br>

- 전체 속성 선택: * 사용 (예: select instructor.*)
- 정렬: ORDER BY 절로 정렬, ASC (오름차순), DESC (내림차순)

```sql
select *
from instructor
order by salary desc, name asc;
```

<br>

### WHERE 절의 조건 표현

<br>

- 비교 연산자: <, <=, >, >=, =, <>
- 논리 연산자: AND, OR, NOT
- 범위 조건: BETWEEN 또는 NOT BETWEEN

```sql
select name
from instructor
where salary between 90000 and 100000;
```

- 튜플 비교: 여러 속성을 한 번에 비교

```sql
select name, course_id
from instructor, teaches
where (instructor.ID, dept_name) = (teaches.ID, 'Biology');
```

<br>

## 5. 집합 연산 (Set Operations)

<br>

### UNION / UNION ALL

<br>

- UNION: 두 쿼리 결과의 합집합(중복 제거)

```sql
(select course_id from section where semester = 'Fall' and year = 2009)
union
(select course_id from section where semester = 'Spring' and year = 2010);
```

- UNION ALL: 중복을 유지한 합집합

<br>

### INTERSECT / INTERSECT ALL

<br>

- INTERSECT: 두 쿼리 결과의 교집합 (중복 제거)

```sql
(select course_id from section where semester = 'Fall' and year = 2009)
intersect
(select course_id from section where semester = 'Spring' and year = 2010);
```

- INTERSECT ALL: 최소 중복 수 만큼 교집합 포함

<br>

### EXCEPT (또는 MINUS) / EXCEPT ALL

<br>

- EXCEPT: 첫 번째 쿼리 결과에서 두 번째 쿼리 결과에 없는 튜플 선택 (중복 제거)

```sql
(select course_id from section where semester = 'Fall' and year = 2009)
except
(select course_id from section where semester = 'Spring' and year = 2010);
```

- EXCEPT ALL: 중복 유지하며 차집합 연산

<br>

## 6. 널 값 (Null Values)

<br>

### Null 값 처리

<br>

- NULL 특성:
  - 산술 연산 시 NULL 포함 시 결과는 NULL
  - 비교 연산 시 NULL과의 비교 결과는 UNKNOWN (세 번째 논리값)
- NULL 검사:
  - `IS NULL` 및 `IS NOT NULL` 사용
  - `distinct` 제거 시 두 NULL 값은 동일한 값으로 간주

<br>

## 7. 집계 함수 (Aggregate Functions)

<br>

### 기본 집계

<br>

- 주요 함수: `AVG()`, `MIN()`, `MAX()`, `SUM()`, `COUNT()`
- 예시:
  - 전체 평균 계산
     ```sql
    select avg(salary)
    from instructor;
    ```
  - 별칭 사용
    ```sql
    select avg(salary) as avg_salary
    from instructor
    where dept_name = 'Comp. Sci.';
    ```

<br>

### 그룹화(GROUP BY)와 HAVING 절

<br>

- GROUP BY: 특정 속성을 기준으로 튜플을 그룹으로 묶음

```sql
select dept_name, avg(salary) as avg_salary
from instructor
group by dept_name;
```

- HAVING 절: 그룹에 대한 조건 지정 (WHERE는 그룹화 전, HAVING은 그룹화 후에 적용)

```sql
select dept_name, avg(salary) as avg_salary
from instructor
group by dept_name
having avg(salary) > 42000;
```

<br>

### NULL과 BOOLEAN 값에 대한 집계 처리

<br>

- NULL 무시: `SUM()`, `AVG()`, 등 집계 함수는 NULL 값을 무시 (단, `COUNT(*)`는 모든 튜플 수를 셈)
- Boolean 집계: `SQL:1999`부터 SOME과 EVERY 함수 도입

<br>

## 8. 중첩 하위 질의 (Nested Subqueries)

<br>

### WHERE 절 내 서브쿼리

<br>

- 집합 멤버십 테스트:
  - `IN` / `NOT IN`

  ```sql
  select distinct course_id
  from section
  where semester = 'Fall' and year = 2009
    and course_id in (
      select course_id
      from section
      where semester = 'Spring' and year = 2010
    );
  ```

<br>

- 집합 비교:
  - `> SOME` (또는 `> ANY`), `> ALL`

  ```sql
  select name
  from instructor
  where salary > some (
    select salary
    from instructor
    where dept_name = 'Biology'
  );
  ```

<br>

### 빈 관계 테스트 (Empty Relations)

<br>

- EXISTS: 서브쿼리 결과가 비어 있지 않으면 `TRUE`

```sql
select course_id
from section as S
where semester = 'Fall' and year = 2009
  and exists (
    select *
    from section as T
    where semester = 'Spring' and year = 2010
      and S.course_id = T.course_id
  );
```

<br>

### 중복 없는 결과 테스트 (UNIQUE / NOT UNIQUE)

<br>

- UNIQUE: 서브쿼리 결과에 중복 튜플이 없으면 `TRUE`

```sql
select T.course_id
from course as T
where unique (
  select R.course_id
  from section as R
  where T.course_id = R.course_id and R.year = 2009
);
```

<br>

- 중복 개수를 세어 조건 검사도 가능

```sql
select T.course_id
from course as T
where 1 <= (
  select count(R.course_id)
  from section as R
  where T.course_id = R.course_id and R.year = 2009
);
```

<br>

### FROM 절의 서브쿼리

<br>

- 서브쿼리를 임시 테이블처럼 사용

```sql
select dept_name, avg_salary
from (
  select dept_name, avg(salary) as avg_salary
  from instructor
  group by dept_name
) as dept_avg
where avg_salary > 42000;
```

<br>

- 서브쿼리 별칭 및 속성 재정의도 가능

```sql
select dept_name, avg_salary
from (
  select dept_name, avg(salary)
  from instructor
  group by dept_name
) as dept_avg(dept_name, avg_salary)
where avg_salary > 42000;
```

<br>

### WITH 절 (공통 테이블 표현식, CTE)

<br>

- 복잡한 쿼리의 가독성을 높이기 위해 임시 테이블 정의

```sql
with max_budget(value) as (
  select max(budget)
  from department
)
select budget
from department, max_budget
where department.budget = max_budget.value;
```

<br>

- 여러 `WITH` 절을 중첩하여 사용할 수 있음

```sql
with dept_total(dept_name, value) as (
  select dept_name, sum(salary)
  from instructor
  group by dept_name
),
dept_total_avg(value) as (
  select avg(value)
  from dept_total
)
select dept_name
from dept_total, dept_total_avg
where dept_total.value >= dept_total_avg.value;
```

<br>

### 스칼라 서브쿼리

<br>

- 단일 값 반환 서브쿼리:
  - `SELECT`, `WHERE`, `HAVING` 절 등에서 값이 필요한 곳에 사용
  - 각 부서의 강사 수를 계산할 때 등 쓰일 수 있음

```sql
select dept_name,
  (select count(*)
   from instructor
   where department.dept_name = instructor.dept_name) as num_instructors
from department;
```
<br>

## 9. 데이터베이스의 변경 (Modification of the Database)

<br>

### 삭제 (DELETE)

<br>

- 특정 조건을 만족하는 튜플 삭제

```sql
delete from instructor
where dept_name = 'Finance';
```

<br>

- WHERE 절 없이 사용 시 테이블의 모든 튜플 삭제

```sql
delete from instructor;
```

<br>

- 서브쿼리 사용 예시: 특정 조건(예: 평균 이하 급여)의 강사 삭제

```sql
delete from instructor
where salary < (select avg(salary) from instructor);
```

<br>

### 삽입 (INSERT)

<br>

- 값의 순서에 따라 삽입

```sql
insert into course
values ('CS-437', 'Database Systems', 'Comp. Sci.', 4);
```

<br>

- 또는, 속성 이름 명시

```sql
insert into course (course_id, title, dept_name, credits)
values ('CS-437', 'Database Systems', 'Comp. Sci.', 4);
```

<br>

- 서브쿼리를 통한 삽입 가능

```sql
insert into instructor
select ID, name, dept_name, 18000
from student
where dept_name = 'Music' and tot_cred > 144;
```

<br>

- **일부 속성에만 값 제공 시 나머지는 `NULL` 할당**

<br>

### 수정 (UPDATE)

<br>

- 조건에 맞는 튜플의 속성 값 수정

```sql
update instructor
set salary = salary * 1.05;
```

<br>

- 조건부 수정

```sql
update instructor
set salary = salary * 1.05
where salary < 70000;
```
```sql
update instructor
set salary = case
  when salary <= 100000 then salary * 1.05
  else salary * 1.03
end;
```

<br>

- 서브쿼리를 활용한 수정

```sql
update student S
set tot_cred = (
  select sum(credits)
  from takes natural join course
  where S.ID = takes.ID
    and takes.grade <> 'F'
    and takes.grade is not null
);
```
