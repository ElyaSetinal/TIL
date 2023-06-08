## **DB vs DBMS**

DB : DataBase, Data의 집합    
DBMS : DataBase Management System, DB를 관리하는 프로그램

- Oracle, MySQL, MariaDB, MsSQL, DB2, MongoDB… 등

DataBase의 자료구조
- 관계형 DB(Relational DB; RDB) : 2차원 Table 형식의 정형화 Data에 최적화, Oracle 등
    - {Key:Value} 형태의 비정형 Data(NoSQL; Not Only SQL), 이미지/동영상 등을 의미, MongoDB 등
- 2차원 Table 가로 열이 컬럼(Column), 세로 행이 레코드(Record) - Null 허용
- Column의 첫 행을 `Column Header`(컬럼 헤더)라 지칭한다.
    
    
    |  | 컬럼(Column) | 컬럼(Column) | 컬럼(Column) |
    | --- | --- | --- | --- |
    | 레코드(Record) | A | A | A |
    | 레코드(Record) | A | A | Null(값이 없음) |

---
---

## **NULL**

‘값이 없음’을 의미
- Null을 연산하면 결과로 Null이 나온다.; 중간에 단 하나라도 들어가면, 모든 결과가 Null, 0과는 다른 개념
- Null값은 연산에 사용할 때 임의의 값으로 변경해서 연산 > 함수 사용
``` SQL
NVL(Column, Value) /*Oracle Only*/
```
 e.g., NVL(A,0) => Column A의 내용 중 Null값이 있으면, 0으로 임시 치환하여 계산한다.
- 기본적으로 컬럼은 Null값을 가질 수 있다. 다만, 설정을 통하여 Null을 허용하지 않으면 가질 수 없다. > 제약조건 이용

오라클(Oracle) 제약조건 타입 5가지
|제약조건|내용|
|----|----|
| Primary Key | 테이블 당 반드시 한 개, 레코드 식별 가능, 자동으로 Index 생성, Unique+Not Null 기능 |
| Unique | 값들이 중복이 되어선 안됨, Null 가능, 자동으로 Index 생성 |
| Not Null | Null 입력 불가; 값 필수, 유일한 제약조건 변경 문법 사용 |
| Check | 비지니스 규칙 설정, 여러가지 조건 중 정해진 조건만 사용하고자 할 때 |
| Foreign Key | Table과 외부 Table 연결; JOIN시 연결 고리로써 사용 |

- Null 조회 시, ‘ is (not) null ’ 연산자 사용
- 정렬(오름차순, 내림차순)시에 최대값(오라클 기준)으로 계산하여 정렬함
- Null 허용 > Not Null (Null 금지) 작업은 설정을 변경하는 것, 변경 문법을 사용
    - ‘허용’이라는 기능이 이미 있기 때문에, 금지 기능으로 변경하는 것이다.

---
---

## **SQL (Structured Query Language)**

RDB 접속시 사용하는 언어, 대소문자 구분 없음

ANSI SQL : DBMS와 독립적인, 모든 DBMS에 사용 가능한 SQL문 <-> DBMS에 종속적인, 특정 DBMS에서만 사용 가능한 SQL문

종류

- DQL(Data Query Language) : 조회어; SELECT, WHERE 등
- DML(Data Manipulation Language) : 조작어; UPDATE, INSERT, DELETE, MERGE(오라클 전용) 등
- TCL(Transaction Control Language) : 트랜잭션 제어어; COMMIT, ROLLBACK 등
    - 트랜잭션(Transaction) : DML과 연관, 여러개의 DML을 하나의 작업으로 동작하게 하는 묶음; 원자성
    - DML과 TCL을 하나의 행위라 생각하자
- DDL(Date Define Language) : 정의어; 객체 생성 및 수정, CREATE, ALTER, DROP 등
    - 오라클 객체 // Table(Data 저장), Index(검색 주소), View(보안 및 SQL문 간소화), Seqeunece(특정 컬럼 Numbering), Synonym(보안; 별칭 설정)

---
---

## **Additional Note**

### 식별자(Identifier)

- 프로그래밍 언어의 단어
- 두가지가 있는데, 시스템이 사전 정의한 단어(예약어; 키워드)와 사용자가 임의로 정의하는 단어(변수)가 있다.
- SQL에는 값도 같이 사용. 수치/문자/날짜

---


### Column에 저장할 수 있는 Data의 종류 및 크기

수치형; number() — 음수는 별도의 자릿수가 있나? 없음. 부호는 그대로    
- 정수형 : number(자릿수); 3, 4, 10, …
- 실수형 : number(전체 자릿수, 소수점 자릿수); 3.0, 2.25, …

문자형; char(), varchar()    
- char(byte) : 고정 길이, 지정된 크기를 반드시 생성, 최대 2000    
- varchar2(byte) : 가변 길이, 저장할 크기 만큼만 생성, byte수는 최대치라고 보면 된다. 최대 4000

<br>

- 영어, 숫자 1byte, 한글 2bytes를 사용한다.
- 오라클에선 ‘’(홑따옴표)으로 감싸는 것으로 문자열을 하나로 묶는다.
- 성능면에선 char가 좋으나, 메모리 효율은 varchar2가 좋다.

날짜형; date
- 문자형과 동일하게 ‘’을 사용하여 묶는다.
- 내부적으로 숫자(수치)로 처리됨

---

### From절 더미 테이블
``` SQL
SELECT ~ FROM Dual;
```
- Oracle에서 From절은 반드시 있어야하는데, 어떤 테이블도 적합한 테이블이 없는 경우에 쓰는 테이블 가칭
- 임의의 Table 관련 작업이 아닌 경우에 사용하는 더미 테이블
    - SELECT 절 단순 연산, 날짜 계산 등

