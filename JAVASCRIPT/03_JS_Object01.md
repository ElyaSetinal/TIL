## **Object, 객체**

> 객체는 속성(변수, Property), 동작(함수, Method) 로 구성된다.

시스템이 제공하는 객체(내장 객체, 빌트인 객체)와, 사용자 정의 객체로 나뉜다.

- 사용하기 위해서는 반드시 명시적으로 생성해야 한다.

- [w3school, JS Reference](https://www.w3schools.com/jsref/default.asp) 객체에 대해서 참조하면 좋은 사이트

<br>

### *vscode에서 JS의 함수 내용 읽기*
``` JS
function x(...n, m?) {
    Statement
}
```
- ...n : parameter를 여러개 줄 수 있다는 의미로, 가변인자라 부른다.
- m? : Option을 나타낸다

<br>

### *Method 호출 방법*
python에서 클래스 내부의 Method, 함수를 접근하는 방법은 두가지가 있다.

``` python
class Class_name:
    def __init__(self):
        pass

    def function1(self):
        pass
    
    @classmethod
    def function2(self):
        pass

ar = Class_name()  # 객체 생성

ar.function1()  # Instance Method 접근, 객체.함수명
Class_name.function2()  # Class Method/Static 접근, 클래스명.함수명

```
JS에서도 동일하게, 객체 함수들은 Instance, Class 로 나뉘어서 동작한다.
- 다만, 대부분은 Instance. Class(Static)은 Number type에 비교적 많다. 

<br>

## **시스템 제공 객체**

> 속성과 동작에 대한 자세한 사항은, 각 데이터형 제목에 걸린 링크 참조

### *Data 관련 객체, Data Object Model*

[수치 Number](https://www.w3schools.com/jsref/jsref_obj_number.asp "W3school Number Reference")

- 생성
    ``` js
    let Variable_name = new Number(10); // 새롭게 수치형 명시. JAVA에서도 new 사용
    // 또는
    let Variable_name = 10  // JS가 자동으로 데이터형을 잡는다.
    ```
    - 이후에 나올 Data Type들이 대부분 이와 같은 형태를 갖는다.
        - new를 사용하여 명시하여 할당하면 object 형으로 반환되고, 단순 값을 할당하면 그에 해당하는 Datatype으로 반환된다.

- Property 및 Method 리스트 확인
    ``` JS
    console.dir(Variable_name);
    // new Number() 방식으로 생성한 변수명만 가능하다.
    ```

- Property, Method 사용
    ``` js
    Number.MAX_VALUE  // 처리 가능한 최대값 출력
    Number.MIN_VALUE  // 처리 가능한 최소값 출력
    Number.parseInt  // 정수형으로 변경, 바꿀수 없는 값이라면 NaN으로 반환
    Number.parseFloat  // 실수형으로 변경
    Number.isNaN  // NaN 확인
    Number.isInteger  // 정수형 확인

    num.toFixed(n)  // 소수점 n자리까지 반올림, Instance Method
    // num은 Number형 변수
    ```

<br>

[문자열 String](https://www.w3schools.com/jsref/jsref_obj_string.asp "W3school String Reference")
- 생성
    ``` JS
    let Variable_name = new String("Hello");  // 새롭게 문자열 명시
    // 또는
    let Variable_name = "Hello";
    ```

- Property 및 Method 리스트 확인
    ``` JS
    console.dir(Variable_name);
    // new String() 방식으로 생성한 변수명만 가능하다.
    ```

- Property, Method 사용
    ``` JS
    // str은 String열 변수

    str.length  // 문자열 길이
    str.charAt(idx) // idx로 색인
    str.concat  // 문자열 연결
    str.indexOf("String")  // 문자로 idx 반환, 없는 문자는 -1로 반환
    str.toLowerCase()  // 전부 소문자
    str.toUpperCase()  // 전부 대문자
    str.substring(Start, End?)  // idx를 사용, 시작부터 지정 끝까지 잘라내기
    str.substr(Start, Length?) // idx와 길이를 사용, 시작부터 지정 길이만큼 잘라내기
    str.replace("Old", "New")  // (old, new), 최초에 나오는 old 문자를 new로 교체
    str.trim()  // 공백 제거
    str.split("Sep")  // sep으로 주어진 구분자로 분리하기, 배열로 반환됨
    str.includes("String", Start?)  // Start|Default=0 부터 지정된 문자열이 포함되어 있는지 확인
    str.startsWith("String", Start?)  // Start|Default=0 부터 지정된 문자열로 시작되는지 확인
    str.endsWith("String", End?)  // End|Default=-1 이 지정된 문자열로 끝나는지 확인
    ```
    - 마우스 오버했을 때, : String, String[] 등으로 끝나는데, 이게 반환되는 데이터 타입을 의미한다.

<br>

[날짜 Date](https://www.w3schools.com/jsref/jsref_obj_date.asp "W3school Date Reference")
- 생성
    ``` JS
    let Variable_name = new Date();
    ```

- Property 및 Method 리스트 확인 
    ``` JS
    console.dir(Variable_name);
    ```

- Property, Method 사용
    ``` js
    // d 는 Date형 변수

    d.getFullYear()  // 시스템의 연도 반환, getYear도 있으나 구버전용
    d.getMonth()  // 0~11로 시스템의 월 반환, +1을 해야 현재 월이 나온다. 
    d.getDate()  // 시스템의 일 반환

    d.setFullYear(yyyy)  // 날짜 변수의 년 설정
    d.setMonth(mm)  // 날짜 변수의 월 설정, 0~11까지의 범위로 들어간다.
    d.setDate(dd)  // 날짜 변수의 일 설정
    ```

<br>

[논리 Boolean](https://www.w3schools.com/jsref/jsref_obj_boolean.asp "W3school Boolean Reference")
- 생성
    ``` JS
    let Variable_name = new Boolean(n);  // 새롭게 논리형 명시
    // 또는
    let Variable_name = Boolean(n);
    ```
    - 0, "", null, undefined, NaN :: Boolean에 넣었을 때, 결과가 false로 나온다.

- Property 및 Method 리스트 확인
    ``` JS
    console.dir(Variable_name);
    // new Boolean() 방식으로 생성한 변수명만 가능하다.
    ```

- Property, Method 사용
    ``` js
    // bool은 Boolean형 변수

    bool.toString() // 결과값을 String으로 반환함
    bool.valueOf()  // 결과값을 boolean으로 반환함, 권장사항
    ```
    - 보통 Boolean은 조건식이 필요한(if문이나 for, while문) 문장에 사용되고, Boolean 생성에서도 언급되었지만 빈 문자열외에는 true로 취급되므로, 조건식에 쓰일 논리값으로 사용하기 위해선 valueOf()를 사용해야 한다.

<br>

[배열 Array](https://www.w3schools.com/jsref/jsref_obj_array.asp "W3school Array Reference")
- 생성
    ``` JS
    let Variable_name = new Array(n1, n2, ..., nX);  // 배열에 들어갈 요소 입력
    // 또는
    let Variable_name = [n1, n2, ... , nX];

    // 빈 배열 생성
    let Variable_name = [];
    ```

- Property 및 Method 리스트 확인
    ``` JS
    console.dir(Variable_name);
    // new Array() 방식으로 생성한 변수명만 가능하다.
    ```

- Property, Method 사용
    ``` JS
    // arr은 Array형 변수

    arr[idx]  // 배열에서 idx의 값 반환, 0부터 시작함
    arr.length  // 배열의 길이

    arr.push(...n) // 배열에 요소 추가, inplace(자체 수정)
    arr[idx] = x  // idx 위치의 요소를 x로 변경
    arr.pop()  // idx가 가장 큰 값(마지막 값)이 삭제됨
    arr.splice(idx, Many?, item1?, item2?, ..., itemX?) // 삭제와 삽입을 동시에 할 경우 사용하는 함수
    /* splice Parameter
        idx : 필수값, 위치 지정
        Many : 옵션, 삭제하려는 개수, 삭제하지 않으려면 0을 입력
        item : 옵션, (삭제하고) idx 위치에 추가할 요소    */
    
    arr.reverse()  // 순서를 역순으로 재배치, inplace
    arr.slice(Start, End)  // Start부터 End-1까지, 부분 배열을 반환함
    arr.indexOf(n)  // 해당되는 요소의 idx를 반환, string과 같음
    arr.join(x)  // 배열에 요소 사이사이에 x를 입력하고 연결함
    /* 배열의 join()은 배열 요소들을 하나의 문자열로 변환할 때 사용한다. 문자열의 split()과 반대 */
    
    arr.sort()  // 배열의 요소들을 오름차순으로 정렬, 하단 추가 사항 있음
    ```

<br>

#### *sort() 사용시 주의점*
- 내림차순으로 정렬하고자 한다면, sort로 정렬하고 reverse를 사용해야 한다.

- 배열의 요소가 두자리 이상 수치형인 경우 sort가 제대로 되지 않는데, 이는 sort()의 기본 방식이 Unicode 변환 정렬 방식이기 때문이다. 수치형을 unicode로 변환하고 가장 최초로 나오는 unicode를 비교하기 때문

    > 15의 unicode는 \&#x0031;\&#x0035; 이고, 2의 unicode는 \&#x0032; 이다.    
    sort()를 사용하면 15의 \&#x0031;과 2의 \&#x0032;를 비교하여 15가 작다고 판단, 정렬하는 것

    따라서 sort 내부에 두 숫자의 차가 음수인지 양수인지 판단하는 아래와 같은 함수를 입력하여 정렬하는 것으로 해결한다. [상세 설명(영문)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort#description)
    

    ``` js
    // 함수명은 임의로 설정함
    // 함수를 별도로 작성하고 넣는 방법
    function compareFn(n, n2) {
        return n - n2; }
    ;
    arr.sort(compareFn);

    // sort()에 함수를 직접 넣는 방법
    arr.sort(compareFn(n, n2) {
        return n - n2 } )

    // n - n2대신 n2 - n을 넣으면 내림차순이 된다.
    ```

