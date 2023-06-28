## **Python**
- Python은 기본적으로 Class로 구성되고이 Class를 통하여 함수에 접근하거나 객체를 생성할 수 있다.

- 파이썬은 단락을 구분할 때 들여쓰기로써 구분하며, 들여쓰기가 맞지 않으면 실행되지 않는다.

<br>

## **Datatype, 자료형**

### *Scalar 자료형*

한 변수에 숫자나 참/거짓 등 하나의 값을 담는 자료형들의 총칭

- Immutable, 변경 불가능한 성질을 가진다.
    - 왜 변경이 불가능한지는 변수 설명시 추가적으로 설명할 예정

|형태|Class 명|예시|
|:---:|:---:|:---|
|정수형|int|3, -1, 0, 0x1B|
|실수형|float|1., 3.14, 3e+2|
|논리형|bool|True, False|
|None|none|None|
|함수|function|def func(): ...|

<br>

### *Group 자료형(Container)*

여러개의 자료를 원소로써 묶어 하나의 변수에 담는 형태의 자료형

대표적인 Iterable 객체들이 여기에 포함된다.

> Iterable : 반복 가능한 객체로, 값을 차례대로 꺼내어 사용할 수 있는 객체를 의미한다.

| 형태 | class 명 | 예시 | 특징 |
| :---: | :---: | :--- | :--- |
| 문자열(String) | str | "abc", 'a' | Iterable, 수정 불가능(Immutable) |
| 리스트(List) | list | [1, 2, 3] | 대괄호, Iterable, 순서 있음, 중복 및 수정 가능 |
| 튜플(Tuple) | tuple | (1, 2, 3) | 소괄호, Iterable, 순서 있음, 중복 가능, 수정 불가능(Immutable) |
| 집합, 셋(Set) | set | {1, 2, 3} | 중괄호, Iterable, 순서 없음, 중복 불가, Immutable인 값만 입력 가능 |
| 딕셔너리(Dictionary) | dict | {1:'a', 2:"b"} | {key:value} 쌍으로 이루어짐, Iterable, Value에는 집합 데이터도 가능, Key는 immutable한 값을 가진다. |

<br>

#### *Datatype의 함수*

상기 되어있는 10개의 자료형은 각각 사용 가능한 함수(메서드)들이 다르며 확인 방법은 아래와 같다.
1. 공식문서 참조, [링크](https://docs.python.org/ko/3/library/stdtypes.html "docs.python.org")
2. print(dir(datatype))

가능한 공식문서를 참조하기를 권장한다.
> 기본적으로 Datatype들은 Class, 객체이기 때문에 직접 사용할 수 없는 네이밍 메서드도 포함되어 있는데, 2번 방식은 그런 메서드까지 전부 보여주기 때문에 처음 보는 환경에서는 난해하다.

<br>

### *Escape Characters(이스케이프 문자)*

문자열 내부에서 특별한 의미를 갖는 문자열로, \ (역슬래시)로 시작된다.

| 형태 | 동작 |
| --- | --- |
| \\\ | 역슬래시 문자 표현 |
| \n | 개행(줄 띄우기), Enter |
| \t | 칸 띄우기, Tab |
| \' | ', 홑따옴표 출력 |
| \" | ", 쌍따옴표 출력 | 

- 따옴표 출력의 경우, ' "A" ' 와 같이 다른 종류의 따옴표로 감싸면 내부의 따옴표가 출력되긴 하지만, 문자열 내부에 따옴표 종류 두 가지가 다 있으면 Escape를 써야한다
    > "A", 'B' => " \\"A\\", \\'B\\'

- 이스케이프를 무시하는 명령어를 Raw String이라고 한다.

    ``` python
    r"c:\\users\\local\\…"
    ```

    - 이스케이프 문자를 포함하는 String 앞에 r을 붙임으로써, 이스케이프 문자를 무시하고 전체를 출력한다.

<br>

## **Variable, 변수**
Data를 저장하는 객체, 이름으로 식별자(Identifier)의 한 종류이다.

> Identifier : 프로그래밍 언어에서 이름을 붙일 때 사용하는 단어로, 변수/함수/클래스/모듈 등 객체를 식별하는데 쓰인다.<br>시스템에서 사전 정의한 식별자를 예약어(Keyword)라 한다.

- 변수로써 사용하기 위해 =(Assignment) 기호를 사용한다.

- 변수명을 사용할 때 몇 가지 규칙이 존재한다.
    > \- 변수명의 첫 글자가 숫자로 시작해서는 안된다.<br>\- 공백을 포함해서는 안된다<br>\- 예약어를 사용할 수 없다.<br>\- 내장 함수를 변수명으로 사용하면, 함수로써의 기능을 사용할 수 없다.

- 파이썬에서 모든 변수는 참조 변수(Reference Variable)이다.

<br>

---

#### *Reference Variable, 참조 변수*

> x = 1

위와 같이 변수를 선언하여 사용할 때, 메모리에 x 라는 변수 영역이 생성되고, 변수 영역과 다른 영역에 1 이라는 값이 입력된다. 값이 들어있는 메모리 영역의 주소가 x 라는 변수 영역에 할당된다.

|변수 영역|--->|데이터 영역|
|--|--|--|
|||메모리 주소 100|

즉, 변수 영역에 값을 직접적으로 입력하는 것이 아닌, 다른 영역에 있는 값의 주소를 변수에 입력하는 방식, 위치를 '참조'를 하게 된다.

> C나 Java가 직원(변수 영역)이 직접 서류(데이터)를 들고 가서 작업해주는 모습이라면, 
Python은 직원(변수 영역)말고 비서(주소 영역)가 서류(데이터)를 들고 와서 작업해주는 모습

- 주소를 알고자 한다면 `id()` 함수를 사용하면 된다.

- Scalar 자료형이나, Group 자료형 일부가 Immutable, 변경 불가능한 이유가 이 특성과 연관이 있다.

- Scalar 자료형 : 새로 값을 입력하면, 기존 값이 들어있는 메모리 영역이 삭제되면서 새로운 값 영역이 생성되고, 변수 영역의 주소는 새로운 값 영역을 참조한다.
<br>즉, 기존것이 '변경'되는 것이 아니라, '새롭게' 쓰이는 것

- Group 자료형 : Group 자료형은 선언하게 되면 변수 영역, 자료형 영역, 요소 영역 세 가지로 작성된다.<br>

    |변수 영역|--->|자료형 영역|--->|데이터(요소)영역|
    |--|--|--|--|--|
    |||메모리 주소 100||메모리 주소 1001|
    
    <br>튜플과 문자열은 새로 작성하여 변수에 입력하면, 자료형을 나타내는 메모리 영역(100)이 삭제되고 **새롭게 작성**(200)이 되는 방식이 되어 값 변경이 되는것으로 보이는 것<br>
        
    |변수 영역|~~--->~~|~~자료형 영역~~|~~--->~~|~~데이터(요소)영역~~|
    |--|--|--|--|--|
    |||~~메모리 주소 100~~||~~메모리 주소 1001~~|
    ||--->|자료형 영역|--->|데이터(요소)영역|
    |||메모리 주소 200||메모리 주소 3041|

    참고로, List는 요소가 수정되었을 때, 요소의 주소값만 바뀌고, 자료형 영역의 주소값은 그대로이다.

    [참고 사이트 - 데이터 사이언스 스쿨, 불변형 자료형과 변형 자료형 ](https://datascienceschool.net/01%20python/02.14%20%ED%8C%8C%EC%9D%B4%EC%8D%AC%EC%9D%98%20%EC%9E%90%EB%A3%8C%ED%98%95.html#id6)

---

<br>

### *기본 변수 사용 방법*

``` python
Variable_name = Value  # int, float, string, list, dict ...

# e.g.
i = 1
p = 3.14
s = "Hello World"
l = [1, 2, 3]
d = {"key1": 1, "key2": 2}
```

좌측의 변수명에 우측의 값을 할당(Assignment)하는 방식이며, = (equal) 기호를 사용한다.

<br>

### *동시 할당, Allocation*

여러 변수에 하나의 값을 할당하거나, 여러 변수에 각각 값을 할당하는 방식

``` python
# 여러 변수에 하나의 값 할당
Variable1 = Variable2 = Variable3 = Value

# e.g.
n = n1 = n2 = 10
```
- 하나의 값을 할당하면, 모든 변수는 같은 주소를 갖는다.


``` python
# 여러 변수에 각각 할당
Variable1, Variable2 = Value1, Value2

# e.g.
a, b = 1, 'B'  # a=1, b='B'
a, b = {1 : 'a', 2 : 'b'}  # a=1, b=2
```

- 변수가 N개이면, 할당될 값도 N개 이어야 한다.
- 할당할 값으로써 dict가 주어지면, 변수에는 Key값이 저장된다.

만약 변수에 비해 값이 많은 경우, 사용하지 않을 값에 대해선 _(Underscore), 더미 변수를 사용하여 할당한다.
``` python
a, _, b = 10, 20, 30  # a=10, b=30
```

<br>

### *변수 데이터 타입 확인*
특정 변수에 대해서 데이터 타입을 알고자 할 때는 type() 함수를 사용한다.

``` python
a = 10
print(type(a))  # <class 'int'>
```

특정 데이터 타입과 비교하여 논리값으로써 사용하고자 할 때는 isinstance() 함수를 사용한다.
``` python
s = "Hello"
print(isinstance(s, str))  # True
```

<br>

## **표준 입출력**

> 입력에 사용할 수 있는 것 : 키보드, 마우스, 태블릿, 마이크, 터치스크린 등<br>출력에 사용할 수 있는 것 : 모니터, 프린터, 스피커 등

입력과 출력에 사용할 수 있는건 다양하게 존재하지만, 표준 입출력은 키보드로 입력하고 모니터로 출력하는, CLI에서 값을 입력받고 출력하는 것을 의미한다고 생각하면 된다.

### *입력*
input() 함수를 사용한다.
``` python
input("Prompt")
```
- Prompt의 내용은 입력 대기상태에서 CLI 화면상에 출력될 내용으로, 어떤 값을 입력할 것인지 설명하는데 주로 사용된다.
- input의 결과는 반드시 str, 문자열로 반환된다.

### *출력*
print() 함수를 사용한다.
``` python
# print(value, ..., sep=' ', end='\n')

print("Contents")
```
- Contents로 표기된, print 내부의 값을 화면에 출력한다.
- sep은 구분자로, 함수내에서 , 를 통하여 여러 값을 출력할 때 값을 구분하는 것을 의미한다. 기본값은 공백
- end는 종결어미로, 함수 내 값을 모두 출력하였을 때 추가되는 문자열이다. 기본값은 개행(New Line)

``` python
print("Test1", "Test2")  # Test1 Test2

# sep 옵션
print("Test1", "Test2", sep='<>')  # Test1<>Test2

# end 옵션
print("Test1", "Test2", end='-_-')
print("Test3", "Test4")
''' 
Test1 Test2-_-Test3 Test4
'''
```

<br>

## **Formatting**

문자열(String; str)의 함수로, 문자열 내부에 값을 입력할 때 사용
> help('FORMATTING') 으로 상세 정보 확인 가능

``` python
# 기본 방식
"Test String : {}".format("Hello!")  # Test String : Hello!
```

- 문자열 내부에 중괄호 ({})를 넣고, 문자열에 format() 함수를 사용한다. format함수 내에 중괄호 위치에 들어갈 값을 입력한다.
- 기본적으로 중괄호가 나온 순서대로 format()함수 내부 값을 순차적으로 입력한다.
    - 순서를 변경하고 싶거나, 특정한 값만 입력하고 싶다면 중괄호 내부에 숫자(Index)를 입력하여 값을 지정한다.
    ``` python
    "Test : {}, {}".format("First", "Second")  # Test : First, Second
    "Test : {1}, {0}".format("First", "Second")  # Test : Second, First
    "Test : {1}, {1}".format("First", "Second")  # Test : Second, Second
    ```

- 값이 소수점일 때, 중괄호 안에 `:(.자릿수)f` 를 사용하여 데이터 타입을 명시한다.
    ``` python
    "Test : {:.3f}".format(3.141592)  # Test : 3.142, 3번째 자리에서 반올림
    "Test : {0:.3f}, {0:.1f}".format(3.141592)  # Test : 3.142, 3.1 :: Index 고정, 자릿수만 다르게
    ```

- key=value를 format으로 주고, key를 사용하여 입력
    ``` python
    "Test : {pie}, {a}".format("pie" = 3.141592, "a" = 10)  # Test : 3.141592, 10
    ```

- 숫자 중간에 , 넣어서 단위 구분
    ``` python
    "Test : {:,}".format(100100100)  # Test : 100,100,100
    ```

- Iterable한 값(String, List, Tuple, Set)을 입력 받을 때, 분리하여 넣기 == Unpacking
    - 입력할 값 앞에 * 기호를 추가한다.
    ``` python
    "Test : {}:{}:{}".format(*"ABC")  # Test : A:B:C
    "Test : {1}:{0}:{2}".format(*"ABC")  # Test : B:A:C , string
    "Test : {0}:{1}:{2}".format(*["A","B","C"])  # Test : A:B:C , list
    "Test : {0}:{1}:{2}".format(*("A","B","C"))  # Test : A:B:C , tuple

    "Test : {}:{}:{}".format(*{"A","B","C"}) 
    # Set은 순서가 없기 때문에, 중괄호 안에 Index를 추가할 수 없다.
    # 값은 중괄호 안에 임의로 입력된다.
    ```

- % 지정 방식, C에서도 사용하는 방식
    - python에서는 자주 사용하지 않는다.
    ``` python
    "name: %s, age: %d, height: %.2f, gender: %c" % ("James", 27, 186.582, "M")
    # name: James, age: 27, height: 186.58, gender: M
    # %s : String, 문자열 || %d : digit, 정수형 || %.f : float, 실수형 || %c : 문자, 단일 문자열

#### *Format String*
.format() 방식에 비하여 좀더 간결하게 작성하는 방식이지만, 문자열은 변수에 값을 입력해야 사용 가능하다.

문자열 앞에 f를 붙여서 format string임을 명시해야 한다.

``` python
name = "Song"
print(f"이름:{name}")  # 이름:Song
```

- 중괄호 내부에서 산술연산, 비교연산 가능
- 변수의 데이터 타입에 해당하는 함수 사용 가능