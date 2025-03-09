# 중급 SQL

---

<br>

## 1. 조인 표현식

### 1-1. 자연조인
  - 상황 : 학생의 정보를 담은 student와 수업을 들은 학생의 ID와 성적을 담은 takes을 통하여 각 학생들이 수강한 과목의 정보를 찾아야 하는 상황
    > SELECT name, course_id    
    > FROM student, takes    
    > WHERE student.ID = takes.ID;
  - 정의 : 두 개의 릴레이션에 대해 수행되고 하나의 릴레이션을 결과로 생산한다. 자연 조인은 릴레이션의 스키마에 나타나는 속성값이 같은 튜플의 짝만을 고려한다.
  - 결과 : 두 릴레이션의 스키마에 나타나는 속성이 반복되지 않고 한 번만 표현된다. 또한 속성들의 순서는 처음에는 두 릴레이션의 스키마에 공통인 속성이 나타나고 두 번째에는 처음 릴레이션의 스키마에만 유일한 속성을 나열하고 마지막으로 두 번째 릴레이션의 스키마에 유일한 속성을 나열한다
  - SQL 질의문:
    - 두 개를 조인할떄 : 
      > SELECT name, course_id   
      > FROM student natural join takes
    - 여러 개 조인시 :
      > SELECT A1,A2,A3 ...   
      > FROM r1 natural join r2 natural join r3 natural join r4
  - **단점** : 각 조인 별로 조건이 다르거나 두 개의 릴레이션 사이에 공통된 속성이 여러개라면 원했던 결과가 나오지 않는다. 따라서 조인 조건을 명확히 해야만 한다.
  - SQL 질의문 :
    - 공통된 속성을 여러개 가진 경우
      > SELECT name, title   
      > FROM (student natural join takes) join course using (course_id)

<br>

### 1-2. 조인 조건
  - ON 조건 : 조인을 수행할 릴레이션에 대한 일반적인 술어를 결정 가능하다. 내부 조인의 경우 WHERE과 동일하게 동작한다.
  - 장점 : 
    1. 외부 조인에서는 WHERE과 다르게 동작하여 더욱 효율적인 SQL문 작성이 가능하다
    2. 조인 조건은 ON에 그외 나머지 부분은 WHERE에 작성하면 SQL 질의에 대한 해석이 더욱 쉬워진다.
  - SQL 질의문 :
    - ON을 활용한 내부 조인 :
      > SELECT *   
      > FROM student join takes    
      > ON student.ID = takes.ID;

<br>

### 1-3. 외부 조인
  - 정의 : 조인의 결과에서 빠질 수 있는 튜플을 널 값을 활용해서 보존하는 조인
  - 유형 :
    - 왼쪽 외부 조인(left outer join)은 left outer join의 왼쪽에 나타난 릴레이션의 튜플만 보존한다.
    - 오른쪽 외부 조인(right outer join)은 right outer join의 오른쪽에 나타난 릴레이션의 튜플만 보존한다.
    - 전체 외부 조인(full outer join)은 두 릴레이션의 모든 튜플을 보존한다.

<br>

### 1-4. 조인의 종류와 조인 조건
  - 조인의 종류 :
    - 내부 조인(inner join)
    - 외부 조인(outer join) :
      - 왼쪽 외부 조인(left outer join)
      - 오른쪽 외부 조인(right outer join)
      - 전체 외부 조인(full outer join)
    - 기본적으로 조인은 내부 조인을 의미하기에 inner를 생략해도 내부 조인이 실행된다.
  - 조인의 조건 :
    - natural : 자연 조인(조인의 조건을 명시하지 않음)
    - using : 조인의 조건을 명시함(속성명이 동일해야함)
    - on : 조인의 조건을 명시함(속성명이 동일하지 않아도 가능함)

<br>

## 2. 뷰

- 상황 : 특정 릴레이션은 보안적으로 중요한 정보를 담고 있기에 전체 정보를 일반적인 직원에게 보여줄 수 없다. 질의 결과를 저장하는것은 낭비가 심하기에 가상의 릴레이션을 만드는 방법이 있다.

### 2-1. 뷰 정의
  - SQL 질의문 :
    - 뷰 생성 방법 :
      > CREATE VIEW v AS (query expression)
  - 장점 : 결과 값을 미리 저장하는것이 아니라 개념적으로 포함하고 있어 데이터적 낭비가 없다. WITH과는 다르게 VIEW를 삭제하기 전까지는 계속 존재한다.

<br>

### 2-2. SQL 질의에서 뷰 사용
  - SQL 질의에서 뷰 사용 : 뷰 이름은 릴레이션 이름이 들어갈 수 있는 모든 자리에 사용될 수 있다. 또한 뷰를 활용하여 뷰를 만들어 내는것도 가능하다.

<br>

### 2-3. 실체화 뷰
  - 실체화 뷰 : 뷰 릴레이션을 저장하는 방법
  - 뷰 관리 방법:
    1. 뷰 관리를 상시 수행 : 뷰를 정의하는 데 사용하는 릴레이션이 수정되면 뷰는 바로 관리되어 최신 상태를 유지한다
    2. 뷰에 접근할때 뷰 관리 수행
    3. 주기적으로 뷰 관리를 수행
  - 장점 : 
    - 뷰를 주기적으로 이용하는 응용 프로그램에서는 뷰를 실체화하여 빠른 응답을 받을 수 있다.
  - 단점 :
    - 갱신과 저장의 과정에서 비용이 발생한다.

<br>

### 2-4. 뷰의 갱신
  - SQL 뷰의 갱신조건
    1. FROM절은 오직 한 개의 데이터베이스 릴레이션을 가져야 한다.
    2. SELECT절은 오직 릴레이션의 속성만 포함해야 하며, 어떠한 표현, 집계, distinct 명세를 가져서는 안된다.
    3. SELECT 절에 나열되지 않은 어떤 속성도 널 값으로 될 수 있어야 한다. 즉 이러한 속성은 not null 조건을 가지거나 주 키 일부여서는 안된다.
    4. 질의는 group by나 having 절을 가져서는 안된다.
  - WITH CHECK OPTION : 뷰의 선언 끝에 붙일수 있으며 해당 조건이 있으면 뷰의 WHERE 조건을 만족하지 않을경우 갱신되지 않는다.
  - 최근에는 트리거 기법을 통해 뷰를 갱신한다.

<br>

## 3. 트랜잭션
  - 정의 : 질의문과 갱신문의 순차로 이루여져 있으며, SQL이 시작되는 순간에 암묵적으로 트랜잭션은 시작된다.
  - 트랜잭션 종류 :
    - Commit work : 현재 수행 중인 트랜잭션을 커밋한다. 수행한 갱신을 데이터베이스에 반영하고 완료시 새로운 트랜잭션을 실시한다.
    - Rollback work : 현재 수행 중인 트랜잭션을 롤백한다. 수행한 갱신을 취소한다. 따라서 데이터베이스의 상태는 트랜잭션의 첫 구문이 실행되기 전으로 돌아간다.
  - 사용 이유 : 데이터베이스의 특징인 원자성을 유지하기 위함이다.
<br>

## 4. 무결성 제약 조건
  - 정의 : 사용자로부터의 데이터베이스 변경이 데이터의 일관성에 손실을 초래하지 않음을 보장하기 위해 이용한다.
  - 사용 방법 :
    1. CREATE TABLE : 과정에서 제약 조건 추가
    2. ALTER TABLE table-name add constraint : 이미 존재하는 릴레이션에 제약 조건 추가, 단 이미 존재하는 모든 행에 대하여 검사 이후 조건 만족시 추가하고 아니면 명령어는 거절된다.

<br>

### 4-1. 단일 릴레이션에 관한 제약 조건
  - 허용되는 제약 조건 :
    1. not null
    2. unique
    3. check

<br>

### 4-2. Not NULL 제약 조건
  - 정의 : 제약 조건이 걸린 속성에서 널 값의 삽입이 불가능하다. 이것은 도메인 제약 조건의 한 예이다.,

<br>

### 4-3. Unique 제약 조건
  - 정의 : 제약 조건이 걸린 속성에서 어떠한 두개의 튜플도 속성의 값이 같을 수 없다. not null을 선언하지 않는 이상 널 값을 가질 수 있다.

<br>

### 4-4. CHECK 절
  - 정의 : 모든 튜플이 충족해야 하는 술어 P를 명시한다.
  - 특징 : 널 값이 CHECK절의 조건을 만족한다면 통과된다. 따라서 NULL을 허용하지 않고 싶다면 NOT NOLL 제약을 지정해야 한다.
  - 배치 :
    1. 단일 속성 제약 조건은 해당 속성과 함께 나열된다.
    2. 복잡한 CHECK 절은 CREATE TABLE 문 끝에 나온다.
  - SQL 질의문:
    - 속성과 함께 나열 되는 CHECK 문 : 
      > CREATE TABLE department   
      > (dept_name    VARCHAR(20),    
      >  building     VARCHAR(15),   
      >  budget       NUMERIC(12,2) CHECK(budget>0),    
      >  PRIMARY KEY (dept_name));
    - CREATE TABLE 문 끝에 작성되는 CHECK 문 :
      > CREATE TABLE section   
      >  (course_id    VARCHAR(8),    
      >   sec_id       VARCHAR(8),   
      >   semester     VARCHAR(6),   
      >   PRIMARY KEY (course_id, sec_id),   
      >   CHECK (semester in ('Fall','Winter','Spring','Summer')));

<br>

### 4-5. 참조 무결성
  - 정의 : 주이진 속성의 집합에 대한 한 릴레이션(참조하는 릴레이션)의 값이 또 다른 릴레이션(참조되는 릴레이션)의 특정한 속성 집합에 반드시 나타나는 경우
  - 유형 : 외래키
  - SQL 질의문:
    - 두 릴레이션의 속성 명이 동일할때 :
      > FOREIGN KEY (dept_name) referebces department
    - 두 릴레이션의 속성 명이 다를때 :
      > FOREIGN KEY (dept_name) referebces department(dept_name2)
  - FOREIGN KEY 위반 시 : 절차를 위반을 유발한 동작을 거절한다.
  - ON DELETE/UPDATE + ~ : 참조 무결성을 위반하여도 명령을 강제 수행하도록 한다.
    - CASCADE : 참조 무결성 위반한 항목들을 참조한 릴레이션에서도 동일하게 삭제한다
    - SET NULL : 참조 무결성 위반한 항목들을 참조한 릴레이션에서는 NULL로 값을 대체한다
    - SET DEFAULT : 참조 무결성 위반한 항목들을 참조한 릴레이션에서는 DEFAULT로 값을 대체한다

<br>

### 4-6. 제약 조건 명명
  - 정의 : 제약 조건에 이름을 붙이는 행위로 제약조건을 삭제할때 유용하다.
  - 방법 : 제약 조건 앞에 CONSTRAINT와 붙이려는 이름을 작성한다.
  - SQL 질의문:
    - 제약 조건 이름 명명 : 
      > salary NUMERIC(8,2) CONSTRAINT minsalary CHECK(salary>29000)    
    - 제약 조건 삭제 :
      > ALTER TABLE instructor DROP CONSTRAINT minsalary

<br>

### 4-7. 트랜잭션 수행 중 무결성 제약 조건 위반
  - 정의 : 모든 트랜잭션을 수행하여야만 무결성 제약 조건을 위반하지 않는 상황에서 트랜잭션 중간에는 필수적으로 무결성 제약 조건 위반이 일어날 수 있다. 이러한 경우를 대비하여 연기기능이 있다. 연기 기능을 사용하면 트랜잭션 마지막에 무결성 제약 조건을 검사한다.
  - SQL 질의문:
    > SET CONSTRAINTS constraint-list DEFERRED

<br>

### 4-8. 복잡한 CHECK 조건과 주장
  - 정의 : SQL 표준에 따르면 무결성 제약 조건을 명시할 수 있는 추가적 구조를 제공한다. 하지만 대부분의 데이터베이스 시스템에서는 이를 제공하지 않기에 실제 사용은 주의를 해야한다.
  - 복잡한 CHECK 조건 : 데이터의 무결성을 보장하고 싶지만 이를 모두 테스트 하는 비용이 너무 클때 유용하다.
  - 주장 : 데이터베이스가 항상 만족하길 원하는 조건을 표현하는 술어이다.
  - SQL 질의문:
    - 주장 :
      > CREATE ASSERTION (assertion-name) CHECK (predicate);
  - 적용 절차 :
    1. 주장 생성
    2. 데이터베이스 시스템이 주장의 타당성 검토
    3. 타당한 경우 데이터베이스 시스템의 수정은 주장을 위반하지 않는 경우에만 적용됨
  
<br>

## 5. SQL의 데이터 타입과 스키마

### 5-1. SQL에서 날짜와 시간 타입
  - 유형 :
    1. date : 연도-월-일로 구성되는 날짜 (EX. '2018-04-25')
    2. time : 시,분,초로 구성되는 시간 (EX. '09:30:00'), TIME WITH TIMEZONE을 사용하면 소수점의 시간까지 확인 가능하다.
    3. timestamp : date와 time의 조합 (EX. '2018-04-25 10:29:01.45') WITH TIMEZONE을 사용하면 시간대 정보 또한 저장된다.
  - 추가 사용가능한 함수 : 
    - year, month, day, hour, minute, second, timezone_hour, timezone_minute를 통해 연,월,일,시,분,초, 시간대 정보를 추출 가능하다.
    - current_date(현재 날짜), current_time(현재 시간), localtime(시간대 제외 지역 시간), current_timestamp(시간대와 같이), localtimestamp(지역 날짜와 시간. 시간대 제외)를 얻을 수 있다.
    - interval은 날짜나 시간을 더하거나 빼면 그 구간만큼의 날짜와 시간을 반환한다.

<br>

### 5-2. 타입 변환 및 서식 함수
  - 타입 변환 : CAST(e AS t)를 통해 표현식 e를 타입 t로 변환 가능하다.
  - 형식 변환 : format, to_char, to_number, to_date, convert등으로 형식을 변환할 수 있다.
  - null 처리 함수 :
    - coalesce(salary, 0) : 는 앞에 작성된 속성이 null일때는 뒤에 작성된 인자로 처리하는 것이다. 하지만 두 인자의 속성이 동일해야 한다는 특징이 있다.
    - decode(salary, null, 'N/A', salary) : 는 첫번째 속성이 2번째 인자와 동일한 값이라면 3번째로 표현하고 그 외에는 4번째로 표현되는 것이다.

<br>

### 5-3. 기본값
  - 정의 : insert문에서 특정 값을 제외하고 insert할 경우 그 값을 null이 아닌 기본값을 입력한다.

<br>

### 5-4. 대형 객체 타입
  - 정의 : 이미지나 비디오와 같은 큰 데이터 항을 도메인으로 하여 저장할때 제공되는 속성이다.
  - 유형 :
    1. CLOB(용량) : 해당 용량 만큼의 큰 문자 데이터를 저장한다
    2. BLOB(용량) : 해당 용량 만큼의 큰 이진 데이터를 저장한다

<br>

### 5-5. 사용자 정의 타입
  - 유형 :
    1. 고유 타입
    2. 정형 데이터 타입
    3. 도메인 타입
  - SQL 질의문:
    - 사용자 고유 타입 정의 :
      > CREATE TYPE Dollars AS NUMERIC(12,2) FINAL;   
      > CREATE TYPE Pounds AS NUMERIC(12,2) FINAL;
    - 도메인 타입 정의 :
      > CREATE DOMAIN Dollars AS NUMERIC(12,2) NOT NULL;   
  - 장점 :
    - 프로그래머의 실수를 방지한다. 위의 예시에서 달러와 파운드는 동일한 형태로 구성되어 있으나 달러형의 값을 파운드 형에 값에 대입할 수 없다. 대입하려면 형 변환을 해야한다.
  - 도메인 vs 사용자 정의 타입:
    1. 도메인은 제약조건을 가질수 있으나 사용자 정의 타입은 불가능하다.
    2. 도메인은 엄격하게 지켜질 필요가 없다. 기초형이 호환가능하다면 달러 도메인은 NUMERIC에서 달러 사용자 타입이나 파운드 사용자 타입에 할당 가능하다.
  
<br>

### 5-6. 고유 키값 생성하기
  - 정의 : ID가 고유한지 판단하기 위해서 계속 해서 증가하는 수치를 부여하여 키값으로 활용
  - SQL 질의문:
    - 고유 키값 생성 :
      > id NUMBER(5) GENERATED ALWAYS AS IDENTITY
  - 특징 : 계속 증가해야 하기 때문에 수치형 키-데이터 값만 사용 가능하다. 또한 insert문에서는 자동으로 생성되는 키 값을 지정하면 안된다.

<br>

### 5-7. CREATE TABLE 확장
  - 정의 : 기존의 스키마를 활용하여 테이블을 생성해야 하는 경우
  - SQL 질의문:
    > CREATE TABLE temp_instructor like instructor;

<br>

### 5-8. 스키마, 카탈로그, 환경
  - 카탈로그 : 릴레이션 이름의 최상위 계층 여러 스키마를 보유
  - 스키마 : 릴레이션과 뷰가 속한 공간. 해당 스키마 안에 요소를 탐색시에는 이름을 붙일 필요가 없고 외부 스키마에 있는 것을 탐색할때는 릴레이션이나 뷰 앞에 스키마의 이름을 붙여야 한다.
  - 환경 : 카탈로그와 스키마는 각 데이터베이스 연결에 대해 설정하는 SQL 환경의 일부이다.

<br>

## 6. SQL의 인덱스 정의
  - 상황 : 한 파일에 존재하는 레코드의 작은 부분을 찾아야 하는 상황에서 전체 파일을 탐색하는 것은 비효율적인 상황
  - 정의 : 릴레이션 속성의 특정 값을 가지고 있는 튜플을 릴레이션의 모든 튜플을 살펴보지 않고도 효과적으로 찾는 자료구조
  - 특징 : 인덱스는 논리 스키마가 아니라 물리 스키마의 일부이다. 데이터를 중복하여 저장하지만 빠른 속도를 보장한다.
  - SQL 질의문:
    - index값 생성 :
      > CREATE INDEX (index-name) ON (relation-name)((attribute-list));
    - index값 제거 :
      > DROP INDEX (index-name);

<br>

## 7. 권한
  - 상황 : 데이터베이스에 대한 읽기, 수정, 삭제, 삽입의 권한을 특정 사용자에게 제한하거나 할당하는 상황

<br>

### 7-1. 특권 부여 및 취소
  - 특정 릴레이션이나 뷰에 대한 특권을 부여하는 것이 가능하다. 각 속성에 대한 권한 부여도 가능하다.
  - SQL 질의문 :
    - 특권 부여 :
      > GRANT (privilege list(EX. SELECT / INSERT / UPDATE / DELETE / ALL PRIVILEGES))   
      > ON (relation name or view name)   
      > to (user / role list);
    - 권한 해제 :  
      > REVOKE (privilege list)   
      > ON (relation name or view name)   
      > to (user / role list);

<br>

### 7-2. 역할
  - 상황 :  특정 유저들이 동일한 유형의 권한이 필요할때 역할을 사용 가능하다.
  - 권한 :
    1. 자신의 역할에 직접 부여된 권한
    2. 자신에게 부여된 역할의 권한
  - SQL 질의문 :
    - 역할 생성 :
      > CREATE ROLE instructor
    - 역할에 권한 부여 :
      > GRANT SELECT       
      > ON takes   
      > to instructor;
    - 역할에 역할 부여 :  
      > CREATE ROLE dean
      > grant instructor to dean;

<br>

### 7-3. 뷰에 대한 권한
  - 정의 : 뷰가 특정 질의를 수행할때의 권한을 제한한다.
  - SQL 질의문 :
    > CREATE VIES geo_instructor AS   
    > (SELECT *   
    >  FROM instructor    
    >  WHERE dept_name = 'Geology');

<br>

### 7-4. 스키마에 대한 권한
  - 정의 : 스키마에 속한 릴레이션의 생성과 삭제, 릴레이션 속성의 추가 및 삭제, 인덱스 추가 및 삭제 등의 권한 부여
  - SQL 질의문 :
    > GRANT REFERENCE (dept_name) on department to Mariano

<br>

### 7-5. 특권 양도
  - 정의 : 특정 릴레이션에 대한 권을 주는 권한 즉 특권을 타 사용자에게도 부여하는것을 의미한다.
  - 특징 : 특권을 양도 받은 상대는 양도받은 특권에 한해서는 타인에게 릴레이션의 권한을 조치할 수 있다.
  - SQL 질의문 :
    > GRANT SELECT on department to Amit WITH GRANT OPTION

<br>

### 7-6. 특권 취소
  - 정의 : 특권을 받은 사람의 권한을 취소한다고 할때, 그 사람이 타인에게 준 권한을 회수할것인지 유지할것인지를 정할 수 있다.
  - SQL 질의문 :
    - 연쇄 회수 방지 및 권한 회수 :
      > REVOKE SELECT on department FROM Amit RESTRICT;
    - 연쇄 회수 :
      > REVOKE SELECT on department FROM Amit CASCADE;

<br>

### 7-7. 행 수준 권한
  - 상황 :  전체 데이터에서 자신의 데이터만 볼수 있게끔 해야하는 상황
  - SQL 질의문 :
    > id = SYS_CONTEXT('USERENV', 'SESSION_USER')