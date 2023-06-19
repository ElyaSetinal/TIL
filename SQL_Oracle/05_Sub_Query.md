## **SubQuery**

Query에는 Select의 의미가 있고, 부(附)라는 의미의 Sub가 붙어있다. :: 부수적 Select

``` SQL
Select ...
From ...
Where ... (Select ... From ... Where ...)
``` 

- 원하는 Data를 하나의 SQL문으로 얻지 못할 때 사용. 두 개 이상의 SQL 문장을 하나로 해결하고 싶을 때

- 필요한 Data가 한 Table에 존재할 때, 한 Table의 특정한 Record만이 필요할 때 : SubQuery
    - 필요한 Data가 여러 Table에 산재되어 있을 때, 혹은 다른 Table의 내용이 전부 필요할 때 : Join
    - 여러 Table에서 정보가 필요할 때도 SubQuery를 쓸 수는 있지만, 코드의 가독성이 떨어진다.

- 적용 가능한 문장 : Select, Insert, Delete, Update, Create  대부분의 SQL문에 사용 가능
    - Select의 결과로 특정한 Value가 나오고, 이 Value를 사용할 수 있는 모든 문장에 사용이 가능하다.
    - 여기서는 Where 절에 사용하는 SubQuery 위주

- 절차
    1. 필요한 SQL 문 확인 (단일 Select 문장 생성) 
    2. 중요한 질문(핵심 구문) 확인 (Main, Sub 구분)  
    3. 중요한 질문에서 서브쿼리 실행 결과가 쓰인 곳을 확인하여 Sub 문 입력 (Subquery 적용)
        
        ``` SQL
        e.g.
        SELECT sal FROM emp WHERE ename='SMITH';  :: Sub, Value = 800
        SELECT * FROM emp WHERE sal  800;                :: Main
        SELECT * FROM emp WHERE sal (SELECT sal FROM emp WHERE ename='SMITH');
        ```

- Main과 sub를 잇는 연산자 사용 시 주의해야 함

<br>

### *Single Row*

단일행 연산자는 SubQuery 실행 결과가 단일 행(Record)이 출력되는 경우에 사용 가능한 것이다.

``` SQL
Select ...
From ...
Where ...  (Select ... From ... Where ...)
```

- Group By와 비슷한 느낌으로, 그룹과 단일의 비교가 불가능하기에 SubQuery에 결과가 단일 행이여야 한다.

- 비교연산자인 <, <=, , =, =, != 을 사용할 수 있다.

- SubQuery에 그룹 함수(max, min, avg, sum, count)가 오더라도, Single Record가 결과로 출력되면 사용 가능

<br>

### *Multi Row*

복수행 연산자는 SubQuery 실행 결과가 복수 행(Record)이 출력되는 경우에 사용 가능한 것이다.

``` SQL
Select ...
From ...
Where ... In, all, ... (Select ... From ... Where ...)
```
 
- Single Row에서 사용하던 비교연산자는 사용할 수 없고, 다중선택의 의미를 가진 In 연산자나 특수한 연산자를 사용한다.

- 복수행 연산자 : all, <all, any, <any, EXISTS
    
    
    | 복수행 연산자 | 동작 내용 |
    | --- | --- |
    |  ALL | 이후에 오는 복수 행 Value(서브쿼리 결과)에 대하여, 모든 값 보다 커야한다. <br>:: 최대값보다 커야 한다. [ (~ MAX())] |
    | < ALL | 이후에 오는 복수 행 Value(서브쿼리 결과)에 대하여, 모든 값 보다 작아야한다. <br>:: 최소값보다 작아야 한다. [< (~ MIN())] |
    |  ANY | 이후에 오는 복수 행 Value(서브쿼리 결과)에 대하여, 아무 값보다 크면 된다. <br>:: 최소값보다 크면 된다. [ (~ MIN())] |
    | < ANY | 이후에 오는 복수 행 Value(서브쿼리 결과)에 대하여, 아무 값보다 작으면 된다.  <br>:: 최대값보다 작으면 된다. [< (~ MAX())] |
    | EXISTS | 이후에 오는 복수 행 Value(서브쿼리 결과)에 대하여, 메인쿼리의 실행 여부 결정 서브쿼리 결과 값이 있는지 없는지 확인하여 하나라도 있으면 실행 |

    - All, Any 연산자 = 비교연산자 + SubQuery문에 Max나 Min 사용