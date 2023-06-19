## **개요**

원하는 컬럼(Data)가 하나의 Table이 아닌 여러 Table에 분산된 경우, Table을 연결하여 원하는 값을 얻을 때 사용하는 명령어

- e.g. A Table에서 a,b,c를, B Table에서 α, β를 가져와서 하나의 Table로 표현 (Logic Table):a, b, c, α, β

- 실제 테이블이 생성되는 것은 아니고, Memory에 있는 논리적 Table이다.

- From절에서 실행되며, 연결해야 할 Table이 N개면 JOIN은 N-1번 실행해야 모두 연결된다.

- 제약조건 중 Primary Key(PK) / Unique (UK), Foreign Key (FK)를 사용한다.
    - (FK)(참조키, 외래키)가 연결고리로써 사용되며, 다른 테이블(Master)의 (PK) or (UK)에 연결되어 다른 Table을 참조 가능
    - (FK)가 있는 Table이 Slave, (PK)/(UK)가 있는 Table이 Master 이다.

- 일치하는 값만 나오는 Join을 Inner Join, 일치하지 않아도 모든 값이 나오는 Join은 Outer Join 이라 한다.

    | Inner | Outer |
    | --- | --- |
    | Natural (Inner) Join | Left Outer Join |
    | (Inner) Join ~ Using | Right Outer Join |
    | (Inner) Join ~ On | Full Outer Join (오라클 전용) |
    | Self Join |  |


## **제약 조건(Constraint) Type**

- 이름(Name)이 아니다. Type

| Type | Desc. | Column Level | Table Level |
| --- | --- | :---: | :---: |
| Primary Key(PK) | 테이블 당 반드시 한 개, 레코드 식별자로써 사용 가능, 자동으로 Index 생성됨<br>Unique(중복 제거) + Not Null(빈 값 없음) 기능.<br> 복합 컬럼(2개 이상의 Column)을 PK로 지정 가능 | OK | OK |
| Unique (UK) | 값들이 중복이 되어선 안됨, Null 가능, Index 자동 생성 | OK | OK |
| Not Null (NN) | Null 입력 불가; 값 필수<br>기존 조건인 허용을 금지하는 것이기 때문에, 제약조건을 추가하기보단 변경에 해당된다. <br>SQLDeveloper에서 Nullable에 No가 되어있지만, PK도 동일한 값을 가지므로 유의할 것 | OK | NO |
| Check (CK) | 비지니스 규칙 설정, 여러가지 조건 중 정해진 조건만 사용하고자 할 때 | OK | OK |
| Foreign Key(FK) | Table과 외부 Table 연결<br>JOIN시 연결 고리로써 사용한 Table에 여러 FK가 존재할 수 있다. 연결 될 Column이 있는 Table이 Master Table<br>Master Table의 PK와 UK만 참조가 가능하다. FK는 참조할 PK/UK의 값이나, Null만 가질 수 있다.<br> :: M_PK에 5가 없는데 FK가 5가 될 수는 없다는 의미 | OK | OK |

<br>

## **Join 공통 속성**

- Select 절의 Column 앞에 Table 위치를 지정할 수 있다. e.g., a.A (a Table의 A Column)

- From 절에서 Table 별칭을 지정할 수 있다. 다만, 별칭이 지정되면 Select 절의 위치지정은 반드시 별칭만을 써야한다.


### *Inner JOIN :: Natural Join*

```SQL 
SELECT [Column1’s Table.]Column1, [Column2’s Table.]Column2, ...
FROM Table1 [Table1 Nick] NATURAL JOIN Table2 [Table2 Nick]
```

- Join 대상 Table에서, 자동으로 공통 Column을 찾아서 연결하는 join 방식

- 공통 Column(FK)는 위치지정이 불가능하다.


### *Inner JOIN :: Using()*

``` SQL
SELECT [Column1’s Table.]Column1, [Column2’s Table.]Column2, ...
FROM Table1 [Table1 Nick] JOIN Table2 [Table2 Nick] USING(Common Column)
```

- USING(Common Column)을 통하여 연결하는 방식

- 직접 FK에 해당되는 Column을 지정하여 연결할 수 있다.

- 여러 테이블이 서로 다른 FK로 연결될 때 유용하다.


### *Inner JOIN :: On()*

``` SQL
SELECT [Column1’s Table.]Column1, [Column2’s Table.]Column2, ...
FROM Table1 [Table1 Nick] JOIN Table2 [Table2 Nick] ON 조건식
```

- Using()보다 더 강하게 조건을 명시. Column명이 서로 다르거나, 정확히 지정해야할 때 유용하다.
    - 다만, 두 Table의 내용을 알고있어야 한다.

- Select 절에 FK로 쓰이는 공통 컬럼이 있다면, 반드시 위치를 지정해야 한다.
    - e.g. Select A, B, slave.C From ~~ On (slave.C = master.C)

- 조건식은 두가지로, 동등 비교(=)를 사용하면 Equi JOIN, 부등 비교를 사용하면 Non-equi JOIN 이라 한다.
    
    ```SQL
    ...
    1. Equi Join : FROM A JOIN B ON A.column = B.column
    2. Non-equi JOIN : FROM A JOIN B ON A.column Between a And b
    ...
    ```

    - Non-equi JOIN시, 범위 조건을 만족하면 연결된다.


### *Inner JOIN :: n-Table Join*

별도의 구문이 있는 것은 아니지만, 여러개의 Table을 연결하는 방법에 대하여 기술

``` SQL
SELECT ...
FROM Table1 JOIN Table2 USING/ON...
            JOIN Table3 USING/ON ...
...
```

- Table1과 2를 Join한 Table을 Table X라 가정하면, 그 Table X와 3을 Join하는 방식으로 여러개의 Table을 결합할 수 있다.

- 과정
    1. From A join B Using … == X

    2. From X join C Using …, 여기에 X = A join B Using을 대입

    3. From A join B Using … Join C Using .…

    - 위와 같은 과정으로 3개 이상의 Table을 연결 할 수있다.

- 동일 Column의 경우 보통 이름_1으로 변경되는 경우가 많으므로, 연결 순서에 유의할 것

- Join하는 방식을 Using과 On 방식 모두 사용(=통일할 필요는 없음)이 가능하므로, 필요에 따라 적절히 변경


### *Inner JOIN :: Self Join*

자기 자신에게 있는 값을 참조해야 할 때, 자기 자신 스스로를 Join하는 방식

``` SQL
SELECT Nick.Column
FROM Table1 Nick1 JOIN Table1 Nick2 ON 조건식
...
```

- 논리 Table을 잘 작성해야 한다. 같은 Table에 서로 다른 별칭을 주는 것이 핵심

- 서로 다른 Header를 연결해야 하므로, Join - On 구문을 사용한다.

    - 조건식 작성시, 순서를 잘 생각해야 한다. FK가 Slave임을 기억하자.


### *Outer JOIN :: Left, Right, Full*

``` SQL
...
FROM Table1 LEFT|RIGHT|FULL OUTER JOIN Table2  USING/ON 조건식
...
```

Inner JOIN이 Null값이 없는 Record만 표시했다면, Outer Join은 Null이 있더라도 모든 Record를 표현한다.

- Inner JOIN들의 JOIN도 (Inner) Join으로, Inner가 생략된 것

- Inner Join - Using/On 방식에 Left, Right, Full Outer만 추가된 방식으로, 상세한 동작은 아래와 같다
    - FROM A LEFT OUTER JOIN B  :: A 테이블만 누락된 것을 표시

    - FROM A RIGHT OUTER JOIN B  :: B 테이블만 누락된 것을 표시

    - FROM A FULL OUTER JOIN B  :: A,B 테이블 모두 누락된 것을 표시 (오라클 전용)

- Left, Right, full 무관하게, Null이 없으면 Inner join과 다를바 없다.

- Where 절에 is Null을 사용함으로써 null 값이 있는 Record만 추출이 가능하다.

    ``` SQL
    ...
    FROM Table1 LEFT|RIGHT|FULL OUTER JOIN Table2  USING|ON 조건식
    WHERE Table1.Column Is Null
    ...
    ```

    - 다만 이 경우, Left인지, Right인지 구분하여 테이블명을 지정해야 한다.