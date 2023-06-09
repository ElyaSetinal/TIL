## **SELECT 절**

데이터를 검색하는 기능

- Projection : 열(Column; 가로) 선택
- Selection : 행(Record; 세로) 선택
- Join : 공통 컬럼을 이용하여 다른 테이블의 데이터 가져오기

<br>

### *모든 Record를 대상으로 검색하는 기능, Projection*

``` SQL
SELECT Column_name, ...
FROM Table;
```
 
- `SELECT`에는 Column, `FROM`에는 Table명이 와야 한다. `SELECT` *은 전체 선택

- 컬럼명만 보고 싶으면, select 다음에 지정하면 된다. 오라클에선 `FROM` 생략 불가능

- 별칭을 설정하여 기존 Header를 변경하여 표기 가능하다. 실제 DB에 반영되진 않음

``` SQL
SELECT Column_name AS "Column.Nick", ...
FROM Table;
```

- 별칭 설정 시에만 ""(쌍따옴표)로 문자열을 하나로 묶어서 사용한다.

    - 일반적인 문자열은 `''`(홑따옴표)을 사용한다. `""` 사용하지 않는다.

- select에서 연산이 가능하나, 단순 표기만 연산될 뿐, 실제 반영되지는 않는다. (논리 Table, 메모리 레벨)

    - NULL 값 계산에 대한 내용은 [01_Basic_Null](https://github.com/ElyaSetinal/TIL/blob/main/SQL_Oracle/01_Basic.md#null)

- select 내 연결은 파이프 연산자 두 개를 붙인 `||` 를 사용한다.

    ``` SQL
    SELECT Data||Data 
    ```
    - Data에는 컬럼, 수치, 문자(문자열) 가능

- 특정 Column에서 중복값을 제거하고 보고 싶으면 `DISTINCT`를 사용한다

    ``` SQL
    SELECT DISTINCT Column_name, ...
    FROM Table
    ```

<br>

### *특정 레코드를 검색하는 기능, Selection :: `WHERE`*

``` SQL
SELECT Column_Name, ...
FROM Table 
WHERE Expression
```

- WHERE 절에는 연산식(조건식)이 들어가야 함

    - 값에서는 대소문자를 구별한다. identifier에서는 구분하지 않음 (Oracle Only)

    - 값으로 Date를 줘도 가능하나, Date 유형은 자체적으로 수로 변환되어 계산된다. 나중 날짜일수록 수가 커짐

    - 문자열을 연산할 때는 ASCII Code를 사용한다. (A:65 a:97)만 기억해도 됨

<br>

### *조건식(Coditional Expression)*

비교 연산자(Comparison Operator) : `=`, `!=`, `>`, `>=`, `<`, `<=` 등   
(프로그래밍 언어와 다르게 ==를 쓰는게 아니다.)

``` SQL
WHERE Data Operator Data
```

- e.g., **WHERE** A > 12

범위 : BETWEEN A AND B, A이상 B이하의 범위 선택

``` SQL
WHERE Data BETWEEN Data AND Data 
```

- e.g., WHERE A BETWEEN a AND b

다중 선택 : IN(A,B,C,…), A또는 B또는 C또는… 선택, OR의 성격을 가진다.

``` SQL
WHERE Data IN(Data1, Data2, ...) 
```

- e.g., WHERE A IN(a, b, c)

Null 확인 : IS NULL, IS NOT NULL

``` SQL
WHERE Data IS NULL
WHERE Data IS NOT NULL
```

포함되는 문자열 : LIKE

``` SQL
WHERE Data LIKE Wildcard+String
```

- e.g., WHERE A LIKE ‘%a_’

<br>

- `%` : 0글자 이상의 문자열 // `_` : 1글자 문자에 해당되는 특별 연산자
- `%A%` : A가 들어가는 아무거나, 글자수 제한 없음
- `_A_` : A 앞뒤 한글자씩, 3글자 제한, _ 의 갯수에 따라서 허용되는 글자수가 다르다.

<br>

논리 연산자(Logical Operator) : AND(그리고), OR(또는), NOT(부정). 다중 조건 선택시에 사용

``` SQL
WHERE Data AND Data OR Data ...
```
- e.g., WHERE A AND B OR C

<br>

- 결과값으로 TRUE와 FALSE, Boolean값으로 Return된다
- NOT의 위치는 중요하다. AND NOT은 되고 NOT AND는 안됨

<br>

## **정렬, Order**

기준에 맞추어서 정렬을 한다. 기본적으로 오름차순을 사용

``` SQL
ORDER BY Column_name or 조건식 [ASC | DESC] 
```
- ASC : 오름차순(기본), DESC : 내림차순;

<br>

- Column에는 별칭 및 순서(Select 절에서 지정한 순서 한정)도 가능하다
- ORDER BY의 Data 중에 Null이 있다면, 이 Null은 최대값으로 계산된다.(Oracle)
- 다중 정렬도 가능 ORDER BY Column1, Column2, …

    ``` SQL
    ORDER BY Column1 or 조건식1, Column2 or 조건식2
    ```

    - Column1으로 우선 정렬 후, Column2를 기준으로 추가 정렬
    - 각 Column에 대하여 정렬 순서를 지정할 수 있다.  ORDER BY Column1 (조건식), Column2 (조건식)
