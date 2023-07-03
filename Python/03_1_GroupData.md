## **Group Data, Container**
> Iterable, 반복 가능한 객체로 값을 차례대로 꺼내어 사용할 수 있는 객체

Iterable인 데이터들에 한정해서, 길이를 확인하는 함수로 len()을 사용한다. 결과로써 int 값을 출력한다.
``` python
length="length ten"
len(length)  # 10
```

인덱싱, 슬라이싱(Indexing, Slicing)
> 순서가 있는, idx가 있는 그룹형 데이터에 특정 값 혹은 범위의 값을 확인할 때 사용한다.<br>사용 가능 데이터 타입 : string, list, tuple

파이썬에서 idx는 항상 0부터 시작하고, 마지막 idx는 (len()-1)이다.
- 역순은 -1부터 시작한다.
``` py
#Indexing 
var[idx]  # 해당되는 idx의 값을 반환
var[-1]  # 마지막 idx의 값을 반환

var[Start|default=0 : End|default=-1 : Step|default=1]  
# Start <= idx < End 범위에서, Step 간격으로 반환한다.
# 값은 비워져도 상관 없으나, 생략할 수는 없다. 
# e.g., 2 step으로 모든 요소를 확인하고 싶을 때는 var[::2]로 써야지, var[2]쓰면 안된다.
```


### *문자열, String*
> 순서가 존재하여 idx 값을 가지며, Immutable한 성질을 갖는다.

생성

``` python
# 일반적으로 사용하는 방법
'String'
"String"

# 여러줄 문자나, 주석 작성시 사용
'''String'''
"""String"""

# 비문자열 데이터를 문자열로 변환하는데 주로 사용
Var = str()
```

- 따옴표나 str() 함수를 사용한다.

함수

> Immutable, 변경 불가능한 데이터이여서 작성되는 모든 함수는 inplace=False(자기 자신이 교체되지 않음, 새로운 값 반환)의 값을 가진다.

``` python
.count(Char|String)  # 함수 내부 문자가 나오는 개수를 int로 반환 
.lower()  # 전부 소문자로 
.upper()  # 전부 대문자로

.lstrip(|Char)  
# idx:0 부터 왼쪽으로 공백을 제거한다. 만약 문자가 있다면 같은 위치서 부터 해당 문자를 삭제한다.
.rstrip(|Char)  
#  idx:-1 부터 오른쪽으로 공백을 제거한다. 만약 문자가 있다면 같은 위치서 부터 해당 문자를 삭제한다.
.strip(|Char)  
# 양쪽 공백을 제거한다.  문자가 있다면 양쪽부터 문자를 제거한다.

.replace(Old, New)  # 문자열에서 Old 값을 New값으로 교체한다. 
.split(Char|String)  # ()안의 문자를 기준으로 하여 문자열을 나누고, 이를 list로 반환한다.

.find(sub, start|default=0, end|default=-1)
# 문자열에서 특정 문자를 찾고, 최초로 나온 문자의 idx를 반환한다. 못찾으면 -1 반환 <> rfind 역순 검색
# start와 end를 넣으면 start <= idx < end 범위에서 문자를 찾는다.

"String".join(Iterable)  
# 함수 내의 Iterable 데이터와 함수 앞 문자를 연결하여 이를 하나의 문자열로 반환한다.
# 이때, 수학의 분배 법칙을 사용하듯이 join 앞 문자를 Itarable 사이에 삽입한다.

center(length, String)  # 지정된 길이만큼 늘리고, 기존 문자열은 중앙에, 나머지는 주어진 문자열로 채움 
ljust(length, String)  #  center와 동일하나 문자열이 왼쪽 정렬
rjust(length, String)  #  center와 동일하나 문자열이 오른쪽 정렬
```

<br>

### *리스트, List*
> 순서가 있어서 idx값을 가지며, 중복 및 수정 가능(Mutable)

생성

``` python
# 일반적인 방식, 대괄호 사용
Var = [1, 2, 3]
Var = ["Text1", None, 3.14]
Var = []  # Empty List
Var = list()  # Empty List

# 다른 데이터를 변환하는데 주로 사용
Var = list("String")
Var = list(Tuple)
```

함수

> Mutable, 수정 가능한 속성이여서 Inplace=True(자기 자신이 교체) 속성을 갖는다.

``` python
.append(data)  # 데이터를 추가한다. idx는 -1(마지막)으로 고정된다.
.insert(idx, data)  # 지정된 idx에 데이터를 추가한다.
.extend(data)  # Merge 개념으로, 데이터를 통합한다.

''' append와 extend의 차이점
append는 데이터가 그대로 입력되는 반면, extend는 데이터의 요소가 입력된다. 
[1,2,3].append([4,5])  ==> [1, 2, 3, [4, 5]]
[1,2,3].extend([4,5])  ==> [1, 2, 3, 4, 5]
'''

.pop(|idx)  # 마지막 값을 추출하여 반환한다. idx가 있다면 해당 값을 추출하여 반환한다.
# 반환하기 때문에, 변수로써 입력 받을 수 있다.
.remove(value)  # 값을 제거한다. 리스트 내에 값이 없다면 에러가 발생한다. 값에 의한 삭제
del List_var[idx]  # idx에 해당되는 값을 삭제한다. 위치에 의한 삭제
.clear()  # 리스트의 모든 요소를 삭제

.count(value)  # 지정된 값의 갯수를 반환
.index(value)  # 지정된 값의 최초 idx를 반환

.reverse()  # 리스트의 순서를 뒤집는다. 
Var = reversed(List_var)  # 원본 객체를 유지한 상태로 뒤집은 리스트를 반환, 그냥은 사용할 수 없고, list로 변환 시켜 사용한다.

.sort(key=|default=None, reverse=|default=False)  # 리스트를 정렬한다.
'''
key=는 어떤 것을 기준으로 삼아서 정렬할지를 결정하는 것으로, 함수나 클래스들이 들어간다.
    함수나 클래스는 callback 방식으로(인자를 선언하지 않고 알아서 사용하는) 작성한다.
    e.g., key=int, [key=int()는 사용하지 않는다.]

reverse=는 역순으로 정렬할 것인지를 결정하는 것으로, True일 시 List_var.sort().reverse() 와 같다.
'''
Vari = sorted(List_var, key=|default=None, reverse=|default=False)
# sort와 같은 동작을 갖지만, 원본을 유지하고 새로운 값을 반환한다.
```

#### *2차원 리스트(2D List)*
리스트 내부에 리스트가 있는 것으로, 수학의 행렬을 표현한 것이라 생각해도 된다.
- 정확하게는 행렬의 형상을 가진것이라 행렬처럼 모든 요소가 차있는 것이 아니라서, idx 선정에 유의해야 한다.
``` py
var = [["1_1","1_2","1_3","1_4"],["2_1","2_2","2_3"]]

'''
      0     1     2     3
0 "1_1" "1_2" "1_3" "1_4"
1 "2_1" "2_2" "2_3"
'''

var[0]  # ["1_1","1_2","1_3"]
var[0][1]  # "1_2"
var[1][3]  # Error, list index out of range
```
- 요소를 받기 위해서 인덱싱과 슬라이싱도 두개를 사용하는데, 앞에 것을 행번호, 뒤에 것을 열 번호로 보면 된다.

#### *깊은 복사, 얕은 복사*
> 리스트는 mutable하여 요소를 수정하는 경우 본인 자체가 변한다. 원본 리스트가 훼손되어 버리는데, 이 원본 리스트를 유지하는 방법으로 깊은 복사를 사용한다.

Basic에서 다루었던 [참조 변수](https://github.com/ElyaSetinal/TIL/blob/main/Python/01_Basic.md#reference-variable-%EC%B0%B8%EC%A1%B0-%EB%B3%80%EC%88%98) 특성으로 인하여 복사하는 방법에 따라 결과가 다르다. 

||주소|메모리 영역 수|원본 변경시 복사본|방법|
|-|-|:-:|-|-|
|얕은 복사|같음|3|같이 변경|직접 할당(y=x)|
|깊은 복사|다름|4|유지|전체 슬라이싱([:]), .copy(), .list()|

- 메모리 영역 수 의 의미
    - 얕은 복사는 주소만 복사되어 변수(주소) 2 + 값 1
    - 깊은 복사는 값도 같이 복사되어 변수(주소) 2 + 값 2

<br>

### *튜플, Tuple*
> List와 비슷하지만, 내부 요소를 바꿀 수 없다는 큰 차이가 있다.<br>순서는 존재하므로, idx가 존재한다.

생성

``` python
# 일반적인 방식, 소괄호 사용
Var = (1, 2, 3)
Var = (10,)  # Element가 1개인 tuple

# 다른 데이터 타입을 튜플로 변환할 때 주로 쓰는 방식
Var = tuple([1, 2, 3]) 
```

함수

> 기본적으로 요소들을 바꿀 수 없기 때문에, 추가, 삭제, 변경 등의 함수가 존재하지 않고, 확인하는 함수만 존재한다.

``` python
.count(data)  # 해당 데이터의 갯수를 반환
.index(data)  # 해당 데이터의 최초 idx를 반환
```
- 기능이 제한적이지만, 리스트에 비해 메모리 용량이 작고 처리 속도가 빠르다.

- 만약 부득이하게 튜플의 요소를 수정하거나 추가, 삭제등을 해야 하는 경우에는 list() 함수를 통하여 리스트로 변경하고, 작업 후에 tuple() 로 되돌리는 작업을 시행해야 한다.

<br>

### *집합, Set*
> 가장 큰 특징으로는 값의 중복이 불가능하고, 순서가 존재하지 않아 idx가 없다는 점이다.

생성

``` python
# 일반적인 방식, 중괄호 사용
Var = {1, 2, 3}

# 변환하거나 빈 집합을 만들 때 사용하는 방식
Var = set()  # Empty Set
Var = set(Immutable Data)
```
- 집합에 입력 가능한 요소는 반드시 Immutable한 값이어야한다.
    - Immutable Data : String, Scalar, Tuple

함수

> idx가 없기 때문에, idx가 필요한 함수들은 사용이 불가능하다.

``` python
.add(data)  # 집합에 요소 추가
.update(Iterable_Data)  # 요소 병합, Iterable 데이터만 사용 가능하다.

'''
add는 내부 Data가 무엇이든 그대로 추가한다. 따라서, Data가 List형태 인 경우 사용이 불가능하다.

{1, 2, 3}.add( (4, 5) )  ==> {1, 2, 3, (4, 5)}
{1, 2, 3}.add( [4, 5] )  ==> Error

update는 Iterable_data의 요소 하나하나를 추출하여 추가한다. Data가 List형태여도 상관은 없지만, 그룹형이 아니면 사용이 불가능하다.

{1, 2, 3}.update( (4, 5) )  ==> {1, 2, 3, 4, 5}
{1, 2, 3}.update( [4, 5] )  ==> {1, 2, 3, 4, 5}
{1, 2, 3}.update(4)  ==> Error
'''

.discard(Value)  # 해당되는 값을 삭제한다. 값이 없으면 동작하지 않는다.
.remove(Value)  # 해당되는 값을 삭제한다. 값이 없으면 에러가 발생한다.
.pop()  # pop() 내부에 값을 넣으면 idx로 취급되기 때문에, 반드시 빈 괄호로 사용한다. 랜덤 추출

Set1.union(Set2)  # 두 집합의 합집합을 구한다.
Set1.intersection(Set2)  # 두 집합의 교집합을 구한다.
Set1.difference(Set2)  # 두 집합의 차집합을 구한다.
Set1.symmetric_difference(Set2)  # 두 집합의 대칭 차집합을 구한다.
# 대칭 차집합 = 합집합 - 교집합
```

- 중복이 불가능하다는 속성으로 인하여, 중복된 값을 제거하고 싶을때 사용하면 용이하다.

<br>

### *딕셔너리, dict; dictionary*
> Immutable한 Key와 Mutable한 Value로 이루어진, 한 쌍의 값, 대응 관계를 나타내는 자료형<br>
JSON에서도 사용된다.

생성

``` python
Var = {"k1":"v1", "k2":"v2"}  # key:value 형식으로 하나의 쌍을 만든다.
Var = dict(k1='v1', k2='v2')  # 대응 관계에 맞추어서 dict형으로 변환된다.

Var = {}  # Empty Dict., Empty Set이 아니다.
Var = dict()
```

함수

> dict는 key를 통하여 접근한다.

``` python
# Var은 dict형의 변수

Var[New_key] = Value  # 새로운 key를 통하여 값을 넣으면 요소가 추가

Var[key] = New_Value  # 기존 key를 통하여 새로운 값을 넣으면 요소가 변경

del Var[key]  # key를 통하여 삭제
Var.pop(key)  # key와 value를 추출, 변수가 있다면 추출된 값이 출력된다. key가 없다면 keyerror를 발생
Var.pop(key, Value)  # keyerror 대신 Value를 반환한다. keyerror가 발생하지 않기 때문에 중단되지 않는다.
Var.clear()  # dict형의 모든 요소를 삭제시키고, 빈 dict형을 반환한다.

Var1.update(Var2)  # 두 dict data를 병합한다. 만약 같은 key가 있다면, Var2의 값으로 수정한다.

Var.keys()  # key 값들을 dict_keys 클래스로 반환한다.
Var.values()  # value 값들을 dict_values 클래스로 반환한다. 
Var.items()  # key와 value를 동시에 dict_items 클래스로 반환한다.

'''
dict_keys, dict_values, dict_items 모두 list()를 사용하여 변환해야지 그 값을 사용할 수 있다.

변환 후 dict_keys, dict_values는 리스트 내부에 일반 값이 있지만, dict_items는 리스트 내부에 튜플로 값이 존재한다.
'''

# 이미 서술한대로 key값을 통하여 Indexing 한다.

Var[key]  # 해당되는 key의 value를 반환한다.
```