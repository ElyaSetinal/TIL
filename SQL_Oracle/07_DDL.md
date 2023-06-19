## **DDL, Date Define/Definition Langauage**

객체의 생성, 수정, 삭제을 하는데 사용되는 명령어

- Table, Index, View, Seqeunece, Synonym // 오라클 객체
    - Index, View, Seqeunece, Synonym는 물리적 DB에 직접 저장되어 사용가능하고, Table을 보조하는 역할을 한다.
    
        | 객체 명 | 용도 |
        | --- | --- |
        | Table | Data 저장 |
        | Index | Table의 검색 속도 향상 |
        | View | 보안 및 복잡한 SQL 간소화. 여러줄의 SQL을 View로 생성 가능 |
        | Sequence | Table의 특정 컬럼 넘버링 == Auto increment(MariaDB) |
        | Synonym | Table의 비휘발성 별칭 (AS~ 나, FROM A a 같은 휘발성이 아님)<br> Table에 별칭을 줌으로써 보안성을 향상 |
- 자동으로 COMMIT이 된다.(Autocommit)

## **DDL :: Create**

새로운 테이블을 생성한다.

- CTAS

    ``` SQL
    Create Table Table_Name
    As
    Select ~ /* 서브쿼리 */
    ```

- Create Table
    
    ``` SQL
    Create Table Table_Name(
    Column1 Datatype,
    Column2 Datatype, ...
    );
    ```

- Datatype : number(), char(), varchar2(), date, 등등

- Default를 사용해서 기본 값을 지정할 수 있다. 지정하지 않으면 Null값이 입력된다.
    
    ``` SQL
    Create Table Table_Name( 
    Column1 Datatype Default Value,
    Column2 Datatype Default Value, ...
    );
    ```

    - 이후 Insert를 통하여 Data를 추가할 때, Default가 있는 Column은 지정하지 않아도 자동으로 채워진다.
    - 주로 고정된 값일 때 사용된다. e.g. ‘남고’에 ‘학생 목록 - 성별’이나 ‘게시글 작성일’ 같은 항목
    - Record 중복 금지 이슈 같은거 주의해야 함

### *Create : Constaint Type*

제약 조건 타입(Constraint Type)을 이용해서 Table에 저장되는 Data의 무결성을 보장

- 기본 선언 방식(컬럼 레벨, 테이블 레벨)
    
    ``` SQL
    /* Column_Level */

    Create Table Table_Name(
    Column_Name Datatype Constraint Constraint_name Constraint_Type 
    /* [제약 조건 선언] [제약 조건 명] [제약 조건 타입] (권장 사항) */
    혹은 Column Datatype Constraint_Type, /* 제약조건 타입 */
    );
    ```
    
    ``` SQL
    /* Table_Level */

    Create Table Table_Name(
    Column_Name Datatype, ... ,
    Constraint Constraint_name Constraint_Type (Column_Name) /* 괄호안에 반드시 Column명 명시 */
    );
    ```

    - 여러 제약 조건을 사용하고 싶을 때, 컬럼 레벨 선언 방식에선 각 컬럼에 선언을 해야하고, 테이블 레벨 선언 방식에서는 제약조건을 같은 방식으로 선언한다.

    - 제약 조건을 삭제하거나 비활성화 할 때, 제약 조건의 이름(제약 조건 명)을 사용한다.

    - 제약 조건 명 권장 사항 : 테이블 명\_컬럼 명\_제약 조건 타입 약자 (Table_name\_Column\_Constratint Type.Abbreviation)

    - 제약조건 이름은 항상 다르게 해야한다. 같으면 에러 발생

---
#### *다시보는 Constraint Type*

| Type | Desc. | Column Level | Table Level |
| --- | --- | :---: | :---: |
| Primary Key(PK) | 테이블 당 반드시 한 개, 레코드 식별자로써 사용 가능, 자동으로 Index 생성됨<br>Unique(중복 제거) + Not Null(빈 값 없음) 기능.<br> 복합 컬럼(2개 이상의 Column)을 PK로 지정 가능 | OK | OK |
| Unique (UK) | 값들이 중복이 되어선 안됨, Null 가능, Index 자동 생성 | OK | OK |
| Not Null (NN) | Null 입력 불가; 값 필수<br>기존 조건인 허용을 금지하는 것이기 때문에, 제약조건을 추가하기보단 변경에 해당된다. <br>SQLDeveloper에서 Nullable에 No가 되어있지만, PK도 동일한 값을 가지므로 유의할 것 | OK | NO |
| Check (CK) | 비지니스 규칙 설정, 여러가지 조건 중 정해진 조건만 사용하고자 할 때 | OK | OK |
| Foreign Key(FK) | Table과 외부 Table 연결<br>JOIN시 연결 고리로써 사용한 Table에 여러 FK가 존재할 수 있다. 연결 될 Column이 있는 Table이 Master Table<br>Master Table의 PK와 UK만 참조가 가능하다. FK는 참조할 PK/UK의 값이나, Null만 가질 수 있다.<br> :: M_PK에 5가 없는데 FK가 5가 될 수는 없다는 의미 | OK | OK |

---

#### *Primary Key; PK*

컬럼 레벨
``` SQL
Create Table Table_Name(
Column_pk Datatype Constraint Constraint_name PRIMARY KEY, ...
 혹은 Column_pk Datatype PRIMARY KEY, ...
);
```

테이블 레벨

``` SQL
Create Table Table_Name(
Column_pk Datatype, ... ,
Constraint Constraint_name PRIMARY KEY (Column_pk) /* 괄호안에 반드시 Column명 명시 */
);
```

한 쌍(Pair)가 PK로써 동작하는 복합 PK 컬럼을 만들 때는, 테이블 레벨에서만 가능하다.

- PK 무결성 확인은 Pair 비교를 통하여 시행한다.
-   ``` SQL
    Constraint Constraint_name PRIMARY KEY (Column1, Column2)
    ```

#### *Unique; UK*

컬럼 레벨

``` SQL
Create Table Table_Name(
Column_uk Datatype Constraint Constraint_name UNIQUE, ...
 혹은 Column_uk Datatype UNIQUE, ...
);
```

테이블 레벨

``` SQL
Create Table Table_Name(
Column_uk Datatype, ... ,
Constraint Constraint_name UNIQUE ( Column_uk ) /* 괄호안에 반드시 Column명 명시 */
);
```

- 복합 컬럼을 UK로 만들때, 테이블 레벨에서만 가능
-   ``` SQL
    Constraint Constraint_name UNIQUE (Column1, Column2)
    ```

#### *Not Null; NN*
- 원래 Null이 가능하던 것이 금지되는 것이라, Not null 만큼은 제약조건을 추가하는 것이 아니라,기존 제약조건을 변경하는 작업이다.

- `Alter table` 이용한 제약조건 추가 문법이, 테이블 레벨 문법과 동일하다. Not Null은 추가할 수 없기에 테이블 레벨 문법을 사용 할 수 없다.

컬럼 레벨
``` SQL
Create Table Table_Name(
Column_nn Datatype Constraint Constraint_name NOT NULL, ...
 혹은 Column_nn Datatype NOT NULL, ...
);
```

#### *Check; CK*
- 비즈니스 규칙 설정. 입력값을 제한하고 싶을 때 사용하는 제약조건이다.

컬럼 레벨

``` SQL
Create Table Table_Name(
Column_ck Datatype Constraint Constraint_name CHECK(조건식), ...
 혹은 Column_ck Datatype CHECK(조건식), ...
);
```

테이블 레벨

``` SQL
Create Table Table_Name(
Column_ck Datatype, ... ,
Constraint Constraint_name  CHECK(조건식)
);
```

- 조건식의 내용에 따라 다중 규칙이 가능하다

#### *Foreign Key; FK*
- Master Table의 PK 또는 UK 컬럼만 참조할 수 있으며, 그 값은 PK 또는 UK의 값, Null만 가능하다.

- Datatype은 동일해야 하고, Slave의 FK와 Master의 PK/UK는 컬럼명은 달라도 상관없으나, 다르게 되면 Natural Join, Using이 불가능하다.
    - 가독성을 위해서라도 가능한 컬럼명이 같게 하는게 좋다.

- FK로 참조하고 있으면, Master쪽에서 Record 및 Table, PK 제약조건의 삭제가 불가능하다
    - Record는 FK 생성시 옵션을 지정하여 삭제할 수 있다. On Delete CASCADE (Slave의 FK Record도 같이 삭제), On Delete Set Null (Slave의 FK를 Null로 변경)
    - Table은 CASCADE CONSTRAINTS 명령어를 통하여 삭제 가능하다. (관련 모든 FK 삭제, FK가 들어있는 Table에 항목이 삭제되진 않는다.)
    - PK 제약조건도 Table 삭제와 동일하게 FK 제약조건을 삭제함으로써 삭제가 가능하다.

컬럼 레벨

``` SQL
Create Table Table_Name(
Column_fk Datatype Constraint Constraint_name References MasterTable_Name (Column_pk or _uk) On Delete CASCADE 혹은 On Delete Set Null, ...
 혹은 Column_fk Datatype References MasterTable_Name (Column_pk or _uk) On Delete CASCADE 혹은 On Delete Set Null, ...
);
```

테이블 레벨

``` SQL
Create Table Table_Name(
Column_fk Datatype, ... ,
Constraint Constraint_name FOREIGN KEY (Column_fk) References MasterTable_Name (Column_pk or _uk) On Delete CASCADE 혹은 On Delete Set Null, ...
);
```

- Slave의 어떤 컬럼이 FK이고, Master의 어떤 컬럼이 PK/UK인지 알려줘야 함
    - 기존 컬럼방식 구문 사이에 FOREIGN KEY(Column_fk) 라는 추가 명령어가 들어간다.

<br>

### *DDL :: Table Truncate*

Table을 절삭할 때 사용, 모든 레코드를 삭제 (테이블을 삭제하는 게 아니라 내용을 삭제, 구조만 남는다.)

DML Delete와의 차이

|  | DELETE | TRUNCATE |
| --- | --- | --- |
| 기능  | Record 삭제 | Record 삭제 |
| ROLLBACK | 가능 | 불가능 |
| 메모리 성능 | 낮음 | 높음 |
- ROLLBACK을 하기 위해서 임시저장소 메모리에 옮겨놓기 때문에, 메모리의 효율이 낮아진다. (공간을 그만큼 잡아먹으므로)

기본 문법
``` SQL
Truncate table Table_name
```

<br>

### *DDL :: Table Update*

Column 추가

``` SQL
Alter table Table_name
Add (Column1 Datatype, Column2 Datatype, …)
```

Column 삭제

``` SQL
Alter table Table_name
Drop (Column1, Column2, …)
```

Data 크기 변경

``` SQL
Alter table Table_name
Modify (Column Datatype) /*  데이터 타입은 동일하게, 크기만 줄이기 */
```
- e.g. number(4) <> number(6) :: 크기를 줄일 때는 Record가 없어야 한다.   
(크기를 축소시 Record를 비워야 한다는 에러메시지 출력)

Data Type 변경

``` SQL
Alter table Table_name
Modify (Column Datatype) /* 데이터 타입을 다르게 */
```
- e.g. number(4) <> varchar2(4) :: Type 변경 시 Record가 없어야 한다.   
(타입 변경시 Record를 비워야 한다는 에러메시지 출력)

제약조건 추가
- Not Null은 추가가 아니라 변경 문법을 사용

``` SQL
Alter table Table_name
Add Constraint Constraint_name Constraint_type(Column)
/* Constraint_type에는 PRIMARY KEY, UNIQUE, CHECK, FOREIGN KEY만 가능 */
```

``` SQL
Alter table Table_name
Modify (Column Datatype Constraint Constraint_name NOT NULL)
/* NOT NULL은 제약조건을 수정하는 것으로 NOT NULL 말고는 변경이 안됨 */
```

제약조건 삭제
- Create : 제약조건 생성시 이름을 지정하는 이유

``` SQL
Alter table Table_name
Drop Constraint Constraint_name
```

``` SQL
Alter table Table_name
Drop PRIMARY KEY 
/* PK는 Table에 단 한 개가 있으므로, 별도의 이름이 필요치 않음 */
```

#### *Delete, Drop시 옵션 조건*

| 옵션 명 | 사용처 | 동작 |
| --- | --- | --- |
| ON DELETE CASCADE | Create, FK | Master의 Record 삭제 시 Slave의 Record도 같이 삭제 |
| ON DELETE SET NULL | Create, FK | Master의 Record 삭제 시 Slave의 FK는 Null |
| CASCADE CONSTRAINTS | Drop, PK, Slave가 있는 Master Table | Master Table 삭제, Slave 고유의 제약 조건만 남음 |
| CASCADE | Drop Constraint, PK.  Slave가 있는 Master Table | Table 유지, Master의 PK와 Slave의 FK 제약 조건만 삭제 |

ON DELETE CASCADE : 마스터 테이블 레코드 삭제시

ON DELETE SET NULL : 마스터 테이블 레코드 삭제시

CASCADE CONSTRAINTS : 마스터 테이블 Drop시, pk를 참조하는 fk 조건 삭제

CASCADE : 마스터 테이블 PK 제약조건 삭제시

<br>

### *View*

Table의 창, 원하는 내용만 보여주도록 하는 일종의 Mask

Actor(User)의 Table 직접 접근을 차단하고, 특정된 정보만 제공한다.

- 생성 (관리자 권한이 있거나, View 생성 권한이 있어야 만들 수 있다.)

    ``` SQL
    Create View view.name
    As
    Select Column1, Column2, …
    From Table;
    ```