## **Operator, 연산자**

### *Numeric Oper., 산술 연산자*

| 연산자 | 동작 | 형식 | 특징 |
| :---: | --- | :---: | --- |
| + | 덧셈 | a + b | 문자열 연산 시, 문자열 결합을 의미 |
| - | 뺄셈 | a - b |  |
| * | 곱셈 | a * b | 문자열 연산 시, 반복 횟수를 의미 |
| / | 나눗셈 | a / b | int끼리 연산해도 float로 결과가 나온다 |
| % | 나머지 | a % b |  |
| // | 몫 | a // b | 소수점을 버린다 |
| ** | 제곱 | a ** b | pow(a,b)와 동일 |

- 몫과 나머지를 한번에 반환하는 함수, divmod(a,b)
> divmod(a,b) == ((a//b), (a%b))

``` python
divmod(a,b) # a를 b로 나눈 몫과, 나머지를 tuple로 반환
```
- 일반적으로 동시 선언 방식(Allocation)을 사용하여, 몫과 나머지를 따로 받는 경우가 많다.
    - floor, mod = divmod(a,b)

<br>

### *Assignment Oper., 대입 연산자*

| 연산자 | 동작 | 형식 | 동일 형식 |
| :---: | --- | :---: | --- |
| += | 더하여 입력 | a += b |a = a + b |
| -= | 빼고 입력 | a -= b |a = a - b |
| *= | 곱하고 입력 | a *= b |a = a * b |
| /= | 나누고 입력 | a /= b |a = a / b |
| %= | 나머지 계산 후 입력 | a %= b | a = a % b |
| //= | 몫 계산 후 입력 | a //= b | a = a // b |
| **= | 제곱 후 입력 | a **= b | a = a ** b |

<br>

#### *Packing, 그룹 변수*
변수와 집합 자료형 내의 데이터 개수가 다를 때, 변수에 그룹형을 선언함으로써 묶어주는 방식

``` python
Variable1, *Variable2 = Group data
```
- Allocation 방식으로 데이터를 할당할 때, 일반적으로 변수의 갯수와 데이터 갯수가 다르면 에러가 발생한다.

- 변수 앞에 * 을 붙임으로써, 변수가 그룹 변수임을 선언하고, 이 변수에 개별 할당되지 않은 모든 데이터를 입력한다.(Packing)
    - Packing 되지 않은 변수와 데이터는 1:1 대응하고, 나머지 데이터들은 Packing 변수에 List로 입력된다.

- \* 이 붙은 Packing 변수는 Allocation 변수 중 하나만 가능하다.

<br>

### *Comparison Oper., 비교 연산자*

| 연산자 | 동작 | 형식 | 특징 |
| :---: | --- | :---: | --- |
| == | Equal | a == b | SQL에서는 = 이다. 변수의 값을 비교하여 판단 |
| != | Not equal | a != b |  |
| > | Greater than | a > b | 초과 |
| >= | Greater than or Equal | a >= b | 이상 |
| < | Less then | a < b | 미만 |
| <= | Less then or Equal | a <= b | 이하 |
| is none | None check | a is none | None을 비교할 때 사용 |

- 결과로 Boolean 값인 True, False로 나온다.

- 동등 비교(Equal)시 두 가지 방식이 있는데, == 과 is 가 있다.
    ``` python
    a == b  # 값만 비교
    a is b  # 주소값도 비교, (a==b)&&(id(a)==id(b))
    # 파이썬의 변수가 참조 변수이기 때문에 주소가 다를 수도 있다
    ```

<br>

### *Logical Oper., 논리 연산자*
- Boolean 값을 연산할 때

| 연산자 | 동작 | 형식 |
| --- | --- | --- |
| and | T로 같아야지만 T | a and b |
| or | T가 하나라도 있으면 T | a or b |
| not | T ↔ F | not a |

- Python에선 True, False가 아니여도 임의의 데이터를 논리값으로 사용이 가능함
> 내부적 False 처리 : 0, None, "", [], (), {}(Empty dict), set()<br> = 내부가 비어있는 그룹형 데이터 및 0, None

<br>

### *Membership Oper., 멤버쉽 연산자*
- 내부에 특정한 값이 존재하는지 확인, IN 연산자 라고도 함
```python
Variable = Group_Data
Target in Variable

#e.g.,
a = [1,2,3]
2 in a  # True
5 in a  # False
```
- 결과는 Boolean(True, False)로 반환된다.

<br>

## **형변환(Translate)**

### *일반 데이터 형변환*
| 함수 | 동작 | 형식 |
| --- | --- | --- |
| int() | Value를 int(정수형)으로 변경 | int(value) |
| float() | Value를 float(실수형)으로 변경 | float(value) |
| bool() | Value를 bool(Boolean)으로 변경 | bool(value) |
- 무조건 변환이 되는것이 아니라, 변환 후 Datatype이랑 맞아야 한다.

<br>

### *그룹 데이터 형변환*
| 함수 | 동작 | 형식 |
| --- | --- | --- |
| str() | Value를 str(문자열)으로 변경 | str(value) |
| list() | Value를 list(리스트)로 변경 |  |
| tuple() | Value를 tuple(튜플)로 변경 |  |
| set() | Value를 set(집합)로 변경 |  |
| dict() | Value를 dict(딕셔너리)로 변경 |  |