## **개요**

브라우저에서 실행되지만, 특정 브라우저에 종속되어 있지 않고, 브라우저에 한정적이지 않다.
브라우저 외부에서 JS를 실행 = node.js

JS 사용 방법
- \<body>의 임의의 위치나, \<head> 태그 내부에 \<script> 태그를 사용하여 작성
- 외부 js파일을 사용할 떄는 \<script scr="">를 사용한다.
- 같은 폴더안에 있으면(같은 레벨) 경로 없이 파일명으로도 연결 가능하다. 또한 상대/절대 경로 모두 사용이 가능하다.

<br>

## **식별자, 데이터, 변수**

### *식별자(Identifier)*

JS에서 먼저 정의한 식별자를 예약어, 키워드라고 부른다.
- break, case, continue...

사용자 정의 식별자
- 첫 문자는 반드시 영문자, _, $로 시작
- 대소문자 구분, 띄어쓰기 사용 불가

<br>

### *데이터(Data Type)*

기본 데이터형(Primitive Data Type; PDT)
- 수치(number), 문자(string), 논리(boolean), undefined(초기화 하지 않음), null, infinite, NaN

참조 데이터형(Reference Data Type; RDT)
- 객체 표현 {key:value}, 배열 표현 [Value1, Value2, ...], 함수-일급객체, 클래스

<br>

### *변수(Variable)*

파이썬에서 사용하던 그 변수와 동일한 기능이지만, 파이썬 변수와 다른 점은 모든 변수가 참조 변수가 아니라 일반 변수도 있다는 점이다.
- 기본 데이터형을 입력하면 기본 변수, 참조 데이터형을 입력하면 참조 변수

변수 선언은 var나 let을 사용하여 선언하고, 선언 후에 값을 입력하여 초기화한다.
- 선언과 동시에 값 초기화도 가능하다. 
- 동시 선언(allocation)도 가능하다.

``` JS
var Variable_Name;
let Variable_Name ; // 변수 선언, undefined로 저장

Variable_Name = Value;  // 변수에 값 할당(초기화)

// Allocation, 동시 선언
var Variable_name1, Variable_name2;
Variable_name1= Value1, Variable_name2= Value2
// 또는
var Variable_name1= Value1, Variable_name2= Value2
```

- 데이터형은 자동으로 지정된다.
- var변수는 함수 단위로 scope, let 변수는 블록 단위 scope
- 데이터 타입 변환이 자유롭고, 변수에 저장되는 데이터형에 의하여 변수 타입이 결정
- typeof 연산자를 사용하여 데이터 타입 확인 가능

<br>

#### *var, let의 차이*

var는 초창기부터 사용한 키워드로, 변수명을 중복하여 선언하는 것이 가능하다.
- 변수명 중복이 가능하다는 얘기는, 재초기화 작업이 가능하다라는 의미지만 식별하는데 문제를 야기시킨다.
- 함수 스코프를 따른다. : 함수 안에서 선언한 변수는 함수안에서만 사용 가능한 지역 변수. 비함수에서 사용하면 전역 변수가 된다.

let은 ECMA6부터 나온 버전으로, 변수명을 중복하여 선언할 수 없다.    
- var 키워드가 가진 문제점을 해결하기 위하여 나온 키워드라, 가능한 let을 사용하는 것을 권장한다.
- 블럭 스코프를 따른다. : 블럭 밖에서 사용 불가, 함수든 아니든 블록이면 무조건 지역 변수

> 함수나 반복문 내용을 구분하는데 C언어나 CSS처럼 { } 를 사용한다. { }의 문장들이 함수/반복문의 내용    
python에서는 들여쓰기로 통하여 내용을 구분했다면, JS에는 { }, 블록(중괄호 내부)으로 구분한다.

함수나 블럭내에서만 사용되는 지역 변수로 사용되지 않고 전역으로 사용하고 싶다면, 함수나 블럭 밖에서 선언하고 초기화해야 한다.(var 이든 let 이든 밖에서 선언해야 함)

#### *Scope, 스코프*

스코프(Scope)는 '범위'라는 의미로, JS에서는 변수에 대해서 접근할 수 있는 범위이다.

```
      ┌ Global 
Scope ┤
      └ Local ─ Function
              └ Block
```
- 기본적으로 전역 스코프(Global scope)와 지역 스코프(Local scope)로 나뉘고, 지역 스코프는 크게 함수 스코프(Function scope)와 블록 스코프(Block scope)로 나뉜다.

전역 스코프(Global Scope)
- 모든 부분(전역)에서 동작하고 접근할 수 있음을 나타내는 범위로, 전역 스코프를 갖는 변수를 전역 변수라고 한다.
- 어떤 함수나 블록안에서가 아닌, 가장 바깥 부분에서 선언되는 경우가 많다.
- 다만, 일반적으로 다른 파일에서 접근할 수는 없다. 소스 파일 단위로 컴파일 되기 때문

지역 스코프(Local Scope)
- 특정 부분(지역)에서 동작하고 접근할 수 있음을 나타내는 범위. 지역 스코프를 갖는 변수를 지역 변수라고 한다.
- 특정 함수나, 블록안을 범위로 갖는 스코프이고, 이러한 범위 내부에서 선언되는 변수들이 대다수이다.

> 어떤 기술(변수)이 있을 때, 이 기술을 전세계 누구나 사용가능하게 오픈 소스로 한다면 전역 스코프, 특허를 내고 보호하며 우리만 쓰겠다 하면 지역 스코프

함수 스코프(Function Scope)
- 지역 스코프의 한 종류로, 변수가 선언된 함수에서만 접근 가능한 범위를 갖는다.
- 함수 외부에서 호출하려고 하면 에러가 발생한다.

블록 스코프(Block Scope)
- 블록은 구분자인 { }의 내부를 의미하며, 블록 스코프는 이러한 블록 내부에서만 접근 가능하다를 의미
- 변수 선언시 let, const를 사용하면 블록 스코프를 따른다.
- 함수내에서, 함수 스코프는 함수의 전역이지만, 블록 스코프는 함수에서도 지역이다.

``` JS
/* Scope, 에러 발생시 Error로 표기 */
var a=0; // Global Variable
let b=1; // Global Variable
console.log(">>", a, b); // >> 0 1

if (true) {
    var c=2;  // Global Variable
    let d=3;  // Local Variable, Block Scope
    ...
};
console.log(">>", c, d); // >> 2 Error


function Scope_Description() {
    var e=4;  // Local Variable, Function Scope
    let f=5;  // Local Variable, Function Scope and Block Scope
    if (true) {
        var g=6;  // Local Variable, Function Scope
        let h=7;  // Local Variable, Block Scope
    };
    console.log(">>", e, f); // >> 4 5
    console.log(">>", g, h); // >> 6 Error
};
console.log(">>", e, f); // >> Error Error
console.log(">>", g, h); // >> Error Error
```

<br>

### *Datatype Check*

python에서 type()을 사용했다면, JS에서는 typeof를 사용한다.

``` JS
typeof(Variable_Name);
// 혹은
typeof Variable_Name;
```

결과를 string, 문자열로 반환한다.

<br>

### *Const Value, 상수*

변수 앞에 const 키워드를 사용하여 상수 변수를 생성한다.

``` JS
const Variable_Name = Value;
```

이후에 같은 변수명을 사용하여 값을 변경하려 해도 변경이 되지 않는다.

<br>

## **Operator, 연산자**

### *Numeric Oper., 산술 연산자*

|연산자|의미|특징|
|:--:|:--:|:--:|
|+|더하기||
|-|빼기||
|*|곱하기||
|/|나누기|나머지도 같이 출력이 된다.|
|%|나머지값 구하기||

- 나누기 연산시, 소수점까지 같이 출력된다.
- 문자열과 +가 되면, 문자열끼리 연결되는 연결 연산자로써 기능한다.
- +를 제외한 나머지 연산자들은 문자열 형태의 수치와 같이 사용되었을 때 실제로 연산이 된다.
    - "10"-3 -> 7, "10"*3 -> 30, ...
    - 데이터가 연산자에 맞게 자동으로 형변환이 된다.
    - 산술 연산자 말고도 다른 연산자에서도 형변환이 된다.

<br>

### *Substitution, 대입 연산자*

|연산자|의미|
|:--:|:--|
|=|오른쪽 값을 왼쪽에 할당|
|+=|더하면서 할당|
|-=|빼면서 할당|
|*=|곱하면서 할당|
|/=|나누면서 할당|
|%=|나머지값을 구하면서 할당|

- 반복문등에서 일정하게 값을 변화시킬 때 유용하다.

<br>

### *Comparison, 비교 연산자*

|연산자|의미|
|:--:|:--|
|>|크다|
|<|작다|
|>=|크거나 같다|
|<=|작거나 같다|
|==|값이 같다|
|!=|값이 같지 않다|

- 결과로 논리값, Boolean(true, false)를 반환한다.

<br>

#### *Equal, Identical 동등 비교*

\== : 값만 비교한다.

\=== : 값과 데이터 타입까지 비교한다.

``` JS
var a = 10;
var c = "10";

console.log("equal:", c==a); // true
console.log("identical:",c===a); // false
```
- 자동으로 형변환이 되는 성질이 있기 때문에, 문자열 "10"과 수치형 10을 비교할 수 있다.
- 변수 선언은 되었으나 할당이 안되어 undefined가 할당된 변수의 경우, 확인하고자 한다면 identical 동등 비교, === 를 써야한다.

<br>

### *Logical, 논리 연산자*

|연산자|의미|설명|
|:--:|:--:|:--|
|&&|and|모두 true면 true|
|\|\||or|하나라도 true면 true|
|!|not|true와 false 반전|

#### *False로 취급되는 값*

0, ""(빈 문자열), null, undefined, NaN

#### *다른 데이터에 논리 연산자 사용*
자바스크립트에서는 boolean으로 반환되는 값이 아니더라도 논리 연산자가 사용이 가능하다.
- 결과로 boolean값을 출력하는 것이 아닌, 조건에 따라 좌측 혹은 우측 값들을 반환한다.

```JS
// 좌측이 true 값을 가짐
console.log("or True:", 10 || "False value"); // 10
console.log("and True:", 10 && "True value"); // "True value"

// 우측이 false 값을 가짐
console.log("or False:", 0 || "False value"); // "False value"
console.log("and False:", 0 && "True value"); // 0
```

좌측 값을 V1, 우측값을 V2라 가정
|논리연산자|V1=true|V1=false|
|:--:|:--:|:--:|
|and|V2|V1|
|or|V1|V2|

<br>

### *INC/DEC Operator, 증감 연산자*
증가 연산자와 감소 연산자를 합쳐서 증감 연산자라 총칭

C언어에서도 동일한 연산자가 존재한다.

증가 연산자
- ++Variable_name : 전치, 증가시키고 변수에 할당
- Variable_name++ : 후치, 변수에 할당되고 증가
> 변수명을 n이라 하면, n = n + 1과 동작은 같으나, 변수에 언제 입력하느냐가 다를 수 있다.

감소 연산자
- --Variable_name : 전치, 감소하고 변수에 할당
- Variable_name-- : 후치, 변수에 할당하고 감소
> 변수명을 n이라 하면, n = n - 1과 동작은 같으나, 변수에 언제 입력하느냐가 다를 수 있다.

변수에 할당하는 시점을 정확하게 이해하고 예측이 가능하면 강력한 기능이지만, 그 전까진 헷갈리게 하는 주범이다.

<br>

### *Ternary Operator, 3항 연산자*
``` python
Variable_name = True_Value if 조건식 else False_Value
```
위 처럼, 조건문을 한 줄에 작성하는 방식을 JS에서도 사용이 가능하다.

``` JS
Variable_name = (조건식)? True_Value : False_Value;
```
형태가 조금 많이 다르므로, 주의할 것

마찬가지로, 중첩 가능하다.
``` JS
Variable_name = (조건식1)? (조건식2)? True2_Value : False2_Value : False1_Value;
```
- 조건식1에서 True면 조건식2로 진행된다. 만일 False면, 조건식2를 신경쓰지 않고 False1_value가 출력된다.

<br>

### *Spread Operator, 배열 분리 연산자*
배열이나 객체 표현(JSON), 문자열 앞에 ...을 추가하여 배열 요소의 값을 펼치는 효과를 얻는다.(explode)
``` JS
...[1,1,1,1,1]|{1:1, 2:2, 3:3}|"Helloworld"
```

- 배열 복사, 특정 배열에 다른 배열 삽입, 값 추가 등에 활용
- 단독적으로 사용하기는 어렵고, 또다른 배열이나 함수등에 입력하는 값으로 활용된다.
- for구문을 활용하여 배열에서 특정 요소를 추출하는 작업등을 대체하기에 유용하다.
