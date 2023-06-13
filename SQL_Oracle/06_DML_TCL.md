## DML, 개요

> Data Manipulation Language, 데이터 조작어

Data를 생성, 수정, 삭제 등의 작업을 하는데 쓰이는 SQL 언어

| DML | 동작 내용 |
| --- | --- |
| INSERT | 새로운 Record 생성(삽입) |
| UPDATE | 기존 Column 수정(갱신) |
| DELETE | Record 삭제 |
| MERGE | (오라클 전용) |

- Select 문장과 동일하게 메모리(논리적 Table)에만 반영
    - Transaction의 성질 중 Atomicity(원자성) : 부분적으로 실행되거나 중단되는 것을 방지. 모두 실행되거나, 모두 취소되거나
    - 메모리 단계 : 연필 작성, 물리적 DB : 볼펜 작성. :: 수정이나 삭제 작업등은 연필이 편하다.
        - 따라서, 메모리 단계의 내용을 실제 DB에 반영하기 위해서는 TCL인 Commit을 사용한다.

<br>

## TCL

> Transaction Control Langage. 트랜잭션 제어 언어

Commit

- 물리적 DB에 반영하기., Save와 유사한 개념
- 특정 DBMS는 자동으로 Commit(Autocommit)을 진행한다.

Rollback

- 변경사항 되돌리기, 메모리 단계에서 작성되어 있는 모든 변경사항을 취소한다.
- Commit하지 않은 모든 변경사항(DML)이 취소. 가장 최근 저장(Commit) 직후로 돌아간다.

DML과 TCL의 작동 순서

1. DML을 이용하여 DBMS에 작업 요청
2. DBMS는 메모리 단계에서, 요청된 작업을 논리적 Table에 작성
3. Commit 혹은 Rollback 사용
    1. Commit: 실제 DB에 반영
    2. Rollback : 논리적 Table에 작성되었던 내용 취소

<br>

## DML 

### Insert

> Table에 새로운 Record를 생성(삽입)

주의사항

> Table Column의 제약조건에 위반되어선 안된다.    
    - PK, UK의 경우 중복되어서는 안됨   
    - Not Null의 경우 값이 반드시 지정되어야 함   
Column의 Data Type에 맞는 데이터가 들어가야 함


문법

- 방법 1. 저장할 Column명을 명시

    ``` SQL
    Insert into Table(Column1, Column2,...) 
    Values(Value1, Value2,...)
    ```

    - 컬럼명에서 선언되지 않은 것들에 대해선 값을 지정하지 않아도 된다.
        - Null값으로 입력되므로, Not Null 제약조건이 있으면 에러가 발생한다.
    - Column과 Value는 1:1 대응. 선언된건 반드시 값이 필요하다.

- 방법 2. 저장할 Column명을 생략

    ``` SQL
    Insert into Table
    Values(Values1, Values2, …, ValuesN)
    ```

    - 테이블의 값들에 대해서 순서에 맞추어 모두 입력해야한다. 
        - 테이블의 컬럼수가 N이면, 값도 N개
    - 가독성 문제로 인하여 잘 쓰진 않음, Null값 안들어감

- 방법 3. CTAS, 기존 존재하는 Table을 이용하여 새로운 Table 생성

    ``` SQL
    Create Table New_Table
    As
    Select *, Column_Name, ... from Old_Table
    (Where 1=2)
    ```

    - Where절은 기존 테이블의 구조만 복사하고 싶을때 추가한다.

    - 제약조건은 복사가 되지 않는다. Create Table은 구조만 가져오는 것이기 때문
        - Not Null은 복사가 된다. 나머지는 안됨 :: PrimaryKey는 복사가 되지 않음 그래서 PK인 dept의 nullable이 복사가 되지 않는다.
        - SQLDeveloper의 Nullable이 반드시 Not Null을 의미하지는 않는다.

    - Create를 사용하기 때문에 자동으로 Commit을 한다.

- Insert - Select문을 이용한 멀티 레코드 작성

    - 서브 쿼리인 select를 이용하여 해당되는 레코드들을 불러와서 집어넣는다.
    - 서브 쿼리에 괄호를 치지 않는다.
    - 입력할 Table이 존재하지 않으면 사용 불가능

### Update
특정 Column(s)을 수정

> Column의 Data Type 일치 및 크기보다 작아야 한다.   
Column의 제약조건에 맞추어야 한다.(e.g. Not Null시 반드시 값을 지정)

문법

- 모든 Record 수정
    
    ``` SQL
    Update Table
    Set Column1=Value1, Column2=Value2, ...
    ```

    - 컬럼에 해당되는 모든 값들이 변경됨. 일반적이진 않음

- 특정 Record만 수정

    ``` SQL
    Update Table
    Set Column1=Value1, Column2=Value2, ...
    Where 조건식 :: Record 지정
    ```

    - 특정 Record를 where 조건식에서 지정하여, 그 Record의 Column이 갖는 값을 변경한다.

### Delete

특정 Record 삭제

>FK(Foreign Key)가 참조하는 값은 삭제가 불가능하다. :: 참조 무결성 제약조건 위반    
    - `FK`는 반드시 `PK`/`UK` 가 갖는 값만 가질 수 있다.    
    - 옵션을 지정하면 삭제는 가능하지만, 

문법

- 특정 레코드 삭제

    ``` SQL
    Delete from Table
    Where 조건식 :: Record 지정
    ```

    - 지정된 Record(s)을 삭제한다

- 모든 레코드 삭제
    
    ``` SQL
    Delete from Table
    ```

    - 일반적이진 않음