## 개요

Function은 다른 프로그래밍 언어와 동일하게, 기능 처리의 역할을 수행

- 한 개 이상의 입력을 받아 기능을 수행한 후, 한 개의 출력값을 반환(Return)하는 것

- 함수마다 요소(Parameter)가 다르므로, 공식문서를 참조하는 것이 좋다. 필수 Param.과 옵션 Param.을 구분할 것

- 함수 동작에 있어서 별도의 해당되는 테이블이 존재하지 않을 때, 임시 테이블(From Dual)을 지정한다.

- Data 종류에 따른 구분
    - 문자 : 길이, 대문자/소문자 변경, 공백제거(TRIM), 특정문자 제거 등
    - 수치 : 반올림, 버림(절삭), 절댓값, 부호 파악 등
    - 날짜 : 현재 날짜, 날짜 간 연산, 마지막 일자 파악 등, DBMS에 의존적
    - 변환 : 날짜 ↔ 문자 ↔ 수치, DBMS에 의존적
    - 기타 : NVL 등

- Data 처리 방식에 따른

    - 단일행 함수(Single Row)
        - 레코드(행) 단위 함수 적용
        - In - Out이 1:1
        - 대부분의 함수들이 Single Row에 속해있다.

    - 그룹행 함수(Group Row)
        - 그룹 단위로 함수가 적용
        - 입력 레코드의 갯수와 출력이 반드시 같지는 않다**. 다만 Out이 In보다 적다.
        - 최대값(max), 최소값(min), 합계(Sum), 평균(Avg), 행갯수(count)

<br>

## Single Row :: Text/String (문자/문자열)

문자열과 관련된 함수

- ANSI에 x라 되어있는 함수들은, Oracle에서만 동작하는 함수

| 함수명 | 파라미터 | 동작 | ANSI | 전체 형상(예시) |
| :--- | :--- | :--- | :---: | :--- |
| Initcap() :: 첫 문자 대문자 | String | 첫 글자를 대문자로, 나머지는 소문자 | x | Initcap('ORACLE SERVER') |
| Lower() :: 소문자 변경 | String | 모든 글자를 소문자로 | v | lower('MANAGER') |
| Upper() :: 대문자 변경 | String | 모든 글자를 대문자로 | v | upper('manager') |
| CONCAT() :: 문자열 연결 | String1, String2 | 문자 연결, ||(파이프 연산자)와 동일 동작 | v | concat('ORACLE','SERVER') |
| Lpad() :: 좌측 문자열 끼우기 | String, length, [Fill] | number만큼의 길이가 되도록 왼쪽에 공백을 생성, [Fill]이 있으면 그 Data를 공백에 입력 | v | lpad('MILLER', 10, '*') |
| Rpad() :: 우측 문자열 끼우기 | String, length, [Fill] | number만큼의 길이가 되도록 오른쪽에 공백을 생성, [Fill]이 있으면 그 Data를 공백에 입력 | v | rpad('MILLER',10, '*') |
| Substr() :: 부분열 반환 | String, index, [length] | 문자열에서 index 위치부터 시작하여 [length]의 길이만큼 문자열 추출, 길이가 없으면 끝까지 | v | substr('000101-3234232', 8, 1) |
| Length() :: 문자열 길이 | String | 문자열의 길이를 반환 | v | length('000101-3234232') |
| Replace() :: 문자열 치환 | string, index, [string] | 문자열에서 특정 문자를 치환, [string]이 없으면 공백으로 치환 됨 | v | replace('JACK and JUE', 'J', 'BL') |
| Instr() :: 특정 문자 위치 반환 | String, Target, Start Position, [n] | 문자열에서 타겟 문자의 위치를 반환, [n]이 있으면 n번째 타겟 문자의 위치를 반환 | v | instr('MILLER' , 'L', 1, 2 ) |
| Ltrim() :: 왼쪽 자르기 | String, [Target] | 첫 문자가 [Target]이 아닐때까지, 왼쪽 문자열 삭제 | x | ltrim('MILLERM', 'M') |
| Rtrim() :: 오른쪽 자르기 | String, [Target] | 끝 문자가 [Target]이 아닐때까지, 오른쪽 문자열 삭제 | x | rtrim('MILLERM', 'M') |
| Trim() :: 자르기 | [Option] Target From String | Option에 따라, 특정 문자(Target)을 자른다. (Leading :: 왼쪽, Trailing :: 오른쪽, Both :: 양쪽) | v | TRIM(both 1 from 111234561111 ) |

<br>

## Single Row :: Number (숫자)

수치와 관련된 함수

| 함수명 | 파라미터 | 동작 | ANSI | 전체 형상(예시) |
| :--- | :--- | :--- | :---: | :--- |
| Ceil() | Number | 올림 | v | ceil(10.1) |
| Floor() | Number | 내림 | v | floor(10.1) |
| Mod() | Number1, Number2 | N1을 N2로 나눈 나머지 값을 반환 | v | mod(10,3) |
| Round() | Number, [Digit] | 반올림, [digit]이 음수면 정수의 자릿수, 양수면 소숫점의 자리수이다. | v | round(456.789, 2) |
| Trunc() | Number, [Digit] | [Digit]이하의 수를 절삭한다. Digit이 양수면 소숫점 자리수 | x | trunc(456.789, -1) |
| Sign() | Number | 부호 식별, 값은 나오지 않는다. | v | sign(10) |

<br>

## Single Row :: Date (날짜)

날짜와 관련된 함수, Oracle에 종속적인 함수가 많다.

| 함수명 | 파라미터 | 동작 | ANSI | 전체 형상(예시) |
| :--- | :---: | :--- | :---: | :---: |
| Sysdate |  | 현재 날짜 반환, 날짜에 연산이 가능함 | x | sysdate |
| Systimestamp |  | 시분초, 도, GMT기준 시간 차이까지 반환. 연산이 가능하나, 시분초가 반환되지 않음 | x | systimestamp |
| Months_between() | Date1, Date2 | D1과 D2의 개월 수 계산, 소수점으로 반환된다. | v | months_between(sysdate+100, sysdate) |
| Add_months() | Date, Number | 날짜에 개월 수를 더한다. | v | add_months(sysdate, 1) |
| Next_day() | Date, Day | 지정된 다음 요일인 날짜를 구한다. 오라클 언어에 따라 day값이 바뀐다. | v | next_day(sysdate, '화') |
| Last_day() | Date | 해당되는 날짜의 마지막 일을 구한다. | v | last_day(sysdate) |
| Round() | Date, [Format] | 날짜를 반올림한다. [Format]이 없으면 시간을 계산 [Format] :: ’YEAR’, ‘MONTH’ | v | round(sysdate, 'YEAR') |
| Trunc() | Date, [Format] | [Format] 이후의 날짜를 절삭한다. | v | trunc(sysdate, 'MONTH') |

<br>

## Single Row :: Translate (변환)

날짜 ↔ 문자 ↔ 수치 변환하는 함수, 날짜 ↔ 수치 직접 변환은 불가능하다.

- 자동 변환(묵시적, 암묵적 변환)

    - 따로 함수를 지정하지 않고, 연산 동작시에 자동적으로 변환이 되는 경우

- 강제 변환(명시적 변환)

    - 함수를 지정하여 명시적으로 변환하는 경우. 특정 기능은 DBMS 종속적이다.
    - 함수에 Format을 입력하여, 지정되지 않은 형식에 대하여 사용이 가능하다. :: e.g. 3,000 , 23년 05월 23일 같이 Oracle에 지정되지 않은 값
    - Format을 지정할 경우, 기본 파라미터와 Format 파라미터는 동일한 형식을 가져야 한다.
    - [공식 문서 링크](https://docs.oracle.com/cd/E11882_01/server.112/e41084/sql_elements004.htm#SQLRF00212)

| 함수명 | 파라미터 | 동작 | ANSI | 전체 형상(예시) |
| :--- | :--- | :--- | :---: | :--- |
| to_number() | String, [Format], [NLSParam] | 문자를 숫자로 변경, String과 [Format]의 형식은 동일해야 한다. | v | to_number('1,000','999,999') |
| to_char() | Number, [Format], [NLSparam] | 숫자를 문자로 변경, [Format]에 정해진 문자를 입력하여 특수기호를 추가 가능 | v | to_char(1000, '$999,999') |
| to_date() | String, [Format], [NLSparam] | 문자를 날짜로 변경, Format에 Y를 쓰게 되면 현재 세기의 연도를, R은 특정 규칙을 따른다. | v | to_date('2023,05,23', 'YYYY,MM,DD') |
| to_char() | Date, [Format], [NLSparam] | 날짜를 문자로 변경 | v | to_char(sysdate,'YYYYMMDD(Dy) A.M. HH12:MI:SS') |
| Extract() | Param From Date | 날짜에서 Parameter에 해당되는 요소를 추출한다. |  | extract(year from sysdate) |

<br>

## Single Row :: Case (조건)

특정 조건이 만족하면 어떤 연산을 하는 프로그래밍 언어의 `if-elif`, `switch-case` 구문

- Case 함수, ANSI

    - When절에서 Boolean이 True면 Then절이 동작하고, False면 다음 When절로 넘어감

    - 동등 비교 :: =의 의미로, When절이 정확히 만족해야 동작한다.
        
        ``` SQL
        Select ~~, 
        Case Column When Value Then Operator    
                    When Value Then Operator   
        ...
                    Else Operator    
        End ”Nickname”
        ```

    - 부등 비교 :: 동등을 포함하는 형태(Between, Like, >, <=, …), 범위 내부면 Then절이 동작
        
        ```SQL
        Select ~~, 
        Case When 조건식 Then Operator
             When 조건식 Then Operator
        ...
             Else Operator
        End ”Nickname”
        ```
         
- Decode 함수, Oracle 종속

    - 동등 비교할 때 사용 가능

        ``` SQL
        Select ~~, 
        Decode (Column, Value1, Operator1, Value2, Operator2, …) ”Nickname”
        ```

<br>

## Group Row :: Group Func.

Record가 그룹으로 묶여야 할 때 사용

- 자동 묶음(묵시적) : 전체 Record가 하나의 그룹으로 묶임
- 명시적 묶음 : `GROUP BY`를 통하여 묶는 위치를 지정, **기본적으로 Null을 무시**하고 연산한다.
    
    
    | Max(Column) | (Column)의 최대값 |
    | --- | --- |
    | Min(Column) | (Column)의 최소값 |
    | Sum(Column) | (Column)의 합계 |
    | Avg(Column) | (Column)의 평균값, 실수형식으로 표현된다. |
    | Count(Column) | (Column)의 총 갯수, *을 사용하여(All Column)이 가능하고, 보통 Null을 무시하기 위해 사용된다. |

<br>

## Group Row :: Group by, Having

Select 절에 그룹 함수 사용시, 명시적으로 지정하는 구문

- 상수나 문자열은 같이 쓸 수 있다.

- Group으로 묶이지 않은 Column과 그룹 함수는 동시에 사용할 수 없다. Record 차이가 나기 때문
    - 이를 해결하기 위해 일반 Column을 묶어줘야 하고, 그때 쓰는 것이 `Group By`

- `Group by`에는 `Select` 절에서 선언된 비그룹 Column을 다 적어줘야 에러가 나지 않는다.
    
    ``` SQL
    e.g. 

    Select A, sum(B) 
    from Table
    Group by A;
    ```
- `Having`은 `Group by`를 수식하는 구문으로, `Group by`의 필터링을 담당한다.

    ``` SQL
    e.g. 
    
    Select A, sum(B) 
    from Table
    Group by A
    Having sum(B)>10;
    ```

    - Select의 Where 절과 유사한 역할이며, Having에 그룹 함수(max, min, sum, avg, count)를 사용할 수 있다.