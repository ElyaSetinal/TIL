## **Object, 객체 :: 시스템 제공 객체, 사용자 정의 객체**

### *Browser 관련 객체, Browser Object Model; BOM*

> 브라우저 시작시 자동으로 생성되는 객체들이다.    

접근하기위해 사용하는 변수명은 객체명을 소문자로 작성하며, 변수명으로 property와 Method를 그대로 사용 가능하다.

[Window](https://www.w3schools.com/jsref/obj_window.asp)

창 자체의 속성
``` JS
var window = new Window(); // 자동 생성
```
- 모든 요소와 객체들의 최상위 객체이다.
- property와 method를 사용할 때, window.을 생략할 수 있다.
    - parseInt()사용할 때, Number. 안붙이면 window 객체라고 했듯이.
    - alert(), prompt(), parseInt(), screen, ...

[Navigator](https://www.w3schools.com/jsref/obj_navigator.asp)

브라우저의 정보, 언어, 구성 등
``` JS
var navigator = new Navigator(); // 자동 생성

navigator.userAgent // 브라우저 정보가 출력, 사용자의 브라우저 정보를 확인
```

[Screen](https://www.w3schools.com/jsref/obj_screen.asp)

화면에 대한 정보
``` JS
var screen = new Screen(); // 자동 생성

screen.height // 화면 높이를 픽셀 단위로 반환
screen.width // 화면 너비를 픽셀 단위로 반환
```

History : 역사라는 의미대로, 방문한 페이지들을 관리
``` JS
var history = new History(); // 자동 생성
```

[Location](https://www.w3schools.com/jsref/obj_location.asp)

URL과 Host등, 주소와 관련된 정보
``` JS
var location = new Location(); // 자동 생성

location.hostname  // 프로토콜(http)와 포트(port), path를 제외한 주소 정보
location.host  // hostname:port 정보 반환
location.port  // port 정보 반환, port는 연결의 상호구분을 위해 사용하는 번호/ 논리적 통로이다.
location.href  // hyper reference, 접근할 수 있는 주소 정보
```


### *Document 관련 객체, Document Object Model; DOM*

> Dom Tree를 이용하여 Node를 접근, 값 변경, 수정, 삭제, 추가    
Document 자체에 대한 속성과 동작들

JS를 통하여 HTML에 접근하기 위해선 DOM Tree가 필요로 한데 HTML의 DOM 렌더링 기본 과정은 아래와 같다.

1. 클라이언트(브라우저)가 서버에 HTML을 요청(Request)
2. 요청한 HTML을 서버에서 응답(Response) 
3. 브라우저가 HTML을 받아 한 줄씩 분석(파싱) 
4. 분석(파싱)의 결과로 DOM Tree를 생성 
5. Document 객체가 생성

> Document 객체가 생성된 시점부터 JS로 HTML, DOM Tree에 접근 및 사용이 가능하게 된다.

method, Dom Tree의 특정 Node를 선택하는 방법
``` JS
// ID로 접근하는 방법
document.gerElementById("ID")

// 선택자로 접근하는 방법
document.querySelector("선택자")
document.querySelectorAll("선택자")
```

- DOM이 생성되지 않으면 JS가 접근할 수 없어서 동작하지 않기 때문에 HTML 문서 하단에 스크립트를 따로 작성하거나, \<Head>-\<Script>에 비동기 옵션 추가 혹은 \<body>에 onload 옵션 혹은 비동기 속성을 사용 한다.

tag에서 필요한 값을 얻을 때 쓰는 종류 3가지
- 태그만 사용 Body 얻기 : \<tag>Body\</tag> 
- 사용자 입력 폼태그명 : \<input type="" value="", ...> >> .폼태그명 ().type, .value 등)
- 속성값 얻기 : \<tag 속성명="속성값"> >> .속성명 (.href 등)

- 사용자의 입력에 따라서 동적인 화면을 구성하고자 할 때, DOM 및 JS가 자주 쓰인다.

#### *Back-tick, \`*
``` JS 
// 문자열을 작성하는 방식에는 3가지가 있다.

" String! " // 쌍따옴표, Quotation Mark

' String! ' // 홑따옴표, Quotation Mark

` String! ` // Back-tick
```
Back-tick의 장점
- 문자 구조 유지 : 닫히기 전까지 모두 문자열로 취급하기 때문에, 라인 변경 및 형상 유지가 가능함
- 변수 사용 : 기존 Quotation Marks는 문자열을 닫고 + 기호로 변수와 연결해야 했지만,  Back-tick은 문자열 내부에 변수를 삽입이 가능하다. ${}을 사용한다.

<br>

### *사용자 정의 객체, JSON*

JSON(JavaScript Object Notation) : JS의 객체 표현이라는 뜻으로, [a,b,c,...] 같은 배열도 포함하지만 일반적으로는 {key:value} 형태를 갖는다.