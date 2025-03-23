# 고급 SQL

이번 장에는 범용 프로그래밍 언어에서 SQL에 접근하는 방법을 살펴본다.

## 5.1 프로그래밍 언어에서 SQL 접근

### 범용 언어와 SQL의 결합이 필요한 이유
SQL로 질의를 작성하는 것이 일반적으로 훨씬 쉽다. 하지만, 

1. **SQL로 표현 불가능한 질의**: SQL은 강력한 선언적 언어이지만, 모든 논리를 커버하지 못할 수 있음.
2. **비선언적 기능 필요**: 예컨대, 사용자 인터페이스와 상호 작용하거나, 보고서를 출력하는 등의 작업은 SQL만으로는 부족함.

따라서, 범용 프로그래밍 언어와 SQL을 결합하기 위한 방법이 있는데 다음과 같다.

- 동적 SQL
  - **개념**: 프로그램이 실행 중에 문자열 형태의 SQL 문을 생성하여 DB에 보내고, 결과를 한 튜플씩 처리할 수 있도록 해줌.
  - **예시**:
      - **JDBC (Java Database Connectivity)**
          - Java에서 DB 연결: `DriverManager.getConnection(...)`
          - SQL 실행: `Statement`/`PreparedStatement` → `executeQuery()` 또는 `executeUpdate()`
          - 결과 처리: `ResultSet` 객체를 이용해 튜플 순회
          - **준비된 문(PreparedStatement)** 사용 시 보안(SQL Injection 방지) 및 성능 향상.
      - **ODBC (Open Database Connectivity)**
          - C/C++ 같은 언어에서 DB 연결과 SQL 실행을 위한 표준 API.
          - `SQLConnect`, `SQLExecDirect`, `SQLFetch` 등 함수로 DB 접근.
      - **Python DB API**
          - 예: `psycopg2`(PostgreSQL), `mysql-connector-python`(MySQL) 등.
          - `connect()`, `cursor()`, `execute()`, `fetchall()` 등의 함수로 동작. 
  
- 내장 SQL로
  - **개념**: C, C++, Java 등 호스트 언어 코드 안에 직접 `EXEC SQL ...;` 문장으로 SQL을 삽입(“임베디드”)하는 방식.
  - **동작**: 전처리기(preprocessor)가 임베디드 SQL을 호스트 언어의 함수 호출 형태로 변환 → 이후 컴파일.
  - **커서(cursor)** 사용: 여러 튜플을 순회하며 결과를 한 튜플씩 처리 가능.
  - **최근 추세**: 보통은 동적 SQL(JDBC, ODBC 등)을 선호하는 경향이 있지만, 특정 환경에선 내장 SQL이 여전히 쓰임.

## 5.2 함수와 프로시저

프로시저와 함수는 “비즈니스 로직”이 데이터베이스에 저장되고 SQL 구문이 실행되도록 해 준다.

비즈니스 규칙을 외부에 저장해 프로시저로 인코딩하는 것에 비해 DB 안의 프로시저에 저장하여 정의하는 것이 유리하다.

예를 들면, 응용 프로그램의 변경 없이 비즈니스 규칙이 변경되는 경우에 단지 그 변경만 허용할 수 있다.

### 5.2.1 SQL 함수 및 프로시저의 선언과 호출

학과의 이름을 받아서 그 학과 교수의 수를 반환하는 함수를 생각해보자.

```sql

create function dept_count (in dept_name varchar(20))
		returns integer
    begin
    declare d_count integer;
        select count(*) into d_count
        from instructor
        where instructor.dept_name = dept_name
    return d_count;
    end
    
--

select dept_name, budget
from department
where dept_count(dept_name) > 12;
```

위와 같이 SQL로 함수를 정의하고 질의에 사용할 수 있다.

```sql

create procedure dept_count (in dept_name varchar(20), out d_count integer)
    begin
        select count(*) into d_count
        from instructor
        where instructor.dept_name = dept_count.dept_name
    end
    
--

declare d_count interger;
call dept_count('Physics', d_count);
```

이와 같이 프로시저를 정의하고 in, out은 각각 입력받을 값과 반환될 값이 저장될 매개변수를 나타냅니다.

SQL 프로시저나 내장 SQL로부터 호출 구문을 통해 호출될 수 있다.

### 5.2.2 프로시저와 함수를 위한 언어 구문

SQL은 범용 프로그래밍 언어의 거의 같은 기능을 가진 다양한 구조를 지원한다.

이러한 구조를 다루는 SQL 표준의 일부분을 **영구 저장 모듈(PSM)**이라고 부른다.

- **변수 선언**: `declare`, **할당**: `set`
- **블록**: `begin ... end`
    - `begin atomic ... end` 를 사용하면 해당 블록 전체가 하나의 트랜잭션 단위로 처리.
- **흐름 제어**:
    - `if ~ then ~ else ~ end if`
    - `while ~ end while`
    - `repeat ~ until ~ end repeat`
    - `for r as ... do ... end for`
- **예외 처리**: `signal`, `handler`를 정의해 예외 발생 시 특별 동작 가능.

## 5.3 트리거

트리거는 데이터베이스에서 발생하는 특정 사건에 대한 반응으로 시스템이 자동으로 수행하는 구문이다.

트리거를 정의하기 위해서는 다음 두 가지를 명시해야 한다.

- 트리거가 실행될 시점을 명시해야 한다. 이것은 트리거가 검사 되어야 하는 **사건**이나 만족되어야 하는 **조건**이다. 트리거가 실행될 때 수행되어야 할 동작을 명시해야 한다.
- 트리거가 실행될 때 수행되어야 할 **동작**을 명시해야 한다.

### 5.3.1 트리거의 필요성

트리거는 SQL의 제약조건 방법을 통해 명세할 수 없는 무결성 제약 조건을 구현하기 위해 사용될 수 있다.

또한, 트리거는 어떤 조건을 만났을 때 알려주거나 어떤 작업을 자동으로 수행시키기 유용한 수단이다.

트리거는 데이터베이스 외부에 대한 갱신을 수행할 수가 없다.

## 5.4 재귀 질의

| course_id | prereq_id |
| --------- | --------- |
| BIO-301   | BIO-101   |
| BIO-399   | BIO-101   |
| CS-190    | CS-101    |
| CS-315    | CS-190    |
| CS-319    | CS-101    |
| CS-319    | CS-315    |
| CS-347    | CS-319    |

다음과 같이 prereq 인스턴스에 대해 생각해보자.

이제 어떤 과목의 직접, 간접적인 선행 과목을 찾고 싶다 하자.

다시 말해 CS-347에 대한 직접적인 선행 과목이나 CS-347의 선행 과목의 선행 과목을 찾고 싶은 것이다.

prereq 릴레이션의 **이행 폐포(transitive closure)**는 pre가 직접, 간접적으로 cid의 선행 과목인 모든 쌍(cid, pre)을 포함하는 릴레이션이다.

계층도에서 비슷한 이행 폐포 계산을 요구하는 응용 프로그램이 많이 있다.

예를들면, 자전거의 모든 부품을 찾는 이런 계층도 질의에 사용된다.

### 5.4.1 반복을 통한 이행 폐포

한 가지 방법으로 반복을 사용하는 것이다.

우선 CS-347의 직접적인 선행 과목을 찾는다, 이후 첫번째 집합에 있는 과목의 선행과목을 찾는다.

이러한 반복은 어떠한 과목도 찾을 수 없을 때까지 반복한다.

[그림 5.14]를 보면 이 작업을 하는 함수를 보면 너무나도 복잡하다!

### 5.4.2 SQL에서 재귀

반복을 사용해서 이행 폐포를 명시하는 것은 당연이 불편하다.

대안적인 방법으로는 **재귀적 뷰** 정의를 이용하는 방법이 있는데 사용하기 더 쉽다.

CS-347에 대한 선행 과목의 집합을 CS-347에 대한 선행 과목에 대한 선행 과목의 집합으로 재귀적으로 정의하기 때문이다.

SQL 표준은 뷰를 표현할 때 with recursive 절을 사용하여 재귀의 제한적인 형태를 제공한다.

예를 들어 이행 폐포를 표현하기 위해 재귀 질의가 사용될 수 있다.

## 5. 고급 집계 기능

### 5.5.1 순위화

1. rank: order by 속서에 대해 동일한 모든 튜플에게 동일한 순위를 준다.
예를들어, 1등, 1등, 3등…..
    
    ```sql
    select ID, rank() over (order by (GPA) desc) as s_rank
    from student_grades;
    ```
    
2. dense_rank: 순서 간의 간격을 만들지 않고 1,2,3….등을 부여한다.
    
    ```sql
    select ID, dense_rank() over (order by (GPA) desc) as s_rank
    from student_grades;
    ```
    

순위화된 값 중에 null값이 존재한다면 null 값은 가장 높은 순위로 처리된다. 따라서 주의가 필요하다.
SQL에서는 nulls first 혹은 nulls last를 사용해 명세를 할 수 있다.

```sql
select ID, rank() over (order by (GPA) desc nulls last) as s_rank
from student_grades;
```

### 5.5.2 윈도우

튜플의 범위에 대한 집계 함수를 계산한다.

예를 들어, 시간의 고정된 범위에 대한 집계를 계산하는 데 유용하다. 여기서 시간의 범위가 **윈도우(window)**라고 불린다.

**윈도우 함수에는 OVER 문구가 키워드로 필수** 포함된다.

```sql
SELECT year,
       AVG(num_credits) 
         OVER (ORDER BY year ROWS 3 PRECEDING) AS avg_total_credits
FROM tot_credits;
```

### 5.5.3 피벗팅

일반적으로 cross-tabulation은 **어떤 릴레이션 R의 특정 속성의 값이 속성이 되는 테이블**이라 할 수 있다.

이러한 속성을 **pivot 속성**이라 부른다.

pivot절 안에 있는 for 절은 
(i) 피벗의 속성과 
(ii) 피벗 결과에 속성 이름으로 출현해야 하는 속성의 값
(iii) 새로운 속석의 값을 계산하는 데 사용되는 집계함수를 명세한다.

또한 주어진 cell에 영향을 미치는 튜플이 하나 이상이라면, pivot절 안에 집계 함수를 통해 해당 값들을 어떻게 처리해야 할지 명시해야 한다.

### 5.5.4 롤업과 큐브

SQL은 **cube와 rollup** 연산을 사용하여 group by 연산자의 일반화를 제공한다.

- **rollup**:
    - 지정된 컬럼들의 “접두사(prefix)” 부분집합에 대해 그룹화.
    - 예: `group by rollup(item_name, color)` →
        - (item_name, color), (item_name), () 총 3가지 그룹 결과를 한 번에 얻음.
- **cube**:
    - 지정된 컬럼들의 **모든 부분집합**에 대해 그룹화.
    - 예: `group by cube(A, B)` → (A,B), (A), (B), () 4가지 그룹.
- **grouping sets**:
    - 필요한 부분집합만 명시적으로 지정 가능.
- **grouping() 함수**:
    - rollup/cube로 인해 생성된 NULL 값을 식별(일반 NULL과 구분).