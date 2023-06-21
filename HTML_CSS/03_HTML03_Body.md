## **Body 태그**

### *Header*

h1부터 h6까지 사용 가능하며, 구조 및 내용 참조를 위하여 사용

글씨 크기를 키우기 위해서 사용하는 것이 아니다.

``` HTML
<body>
    <h1>Header 1</h1>
</body>
```

<br>

### *p*

문단을 지정할 때 사용하며, 빈 여백 작성이나 내용 분리의 목적으로 사용하지 않는다.

대표적인 블럭스타일로, 여러 p 태그가 있으면, 각 문단은 세로로 쌓인다.

``` HTML
<body>
    <p>Paragraph1</p>
    <p>Paragraph2</p>
</body>
```

<br>

### *hr*

내용을 분리하기 위해 수평선을 생성하는 태그로, 종료 태그가 없다.

``` HTML
<p>문장</p>
<hr>
<p>문장</p>
<hr size="3" noshade>  <!-- 수평선의 스타일을 지정 -->
```

<br>

### *br*
새로운 개행을 만들 때나, Inline 스타일 태그를 블록 스타일로 변경시 사용한다.

종료 태그가 필요하지 않다.

``` HTML
<body>
    <br>
</body>
```


### Textformat
*텍스트를* 꾸미거나 강조하는데 쓰이는 태그들로, 보통은 이 태그를 쓰기보다는 CSS를 사용한다.

``` HTML
<body>
    <b>Bold</b><br>
    <i>Italic</i><br>
    ...
</body>
```

### *a*, Anchor

닻 이라는 의미로 외부 웹페이지로 이동하거나, 내부의 특정 위치로 이동하는 기능이 있다.
보통 href라는 속성과 함께 사용한다.

``` HTML
<!-- 외부 이동시 -->
<a href="HyperLink" title="Description" target="_blank">Body</a>
```
- href : 이동할 주소 혹은 다른 html 파일
- title : 마우스 오버시에 뜨는 설명창의 내용
- target="_blank" : 새창에서 열기. target은 어디서 문서가 열릴것인가 명시하는 속성

``` HTML
<!-- 내부 이동시, id값과 #을 사용한다. -->
<a href="#AAA">Body</a> <!-- id가 AAA인 위치로 이동-->
...
<a id="AAA"> Targer </a> <!-- 여기로 이동 된다. -->
```

``` HTML
<!-- 외부, 내부 혼합 -->
<a href="Link#AAA">Body</a> <!-- Link html이나 도메인 페이지 등에서 id가 AAA인 위치로 이동-->
...
<!-- Link 위치 -->
<a id="AAA"> Targer </a> <!-- 여기로 이동 된다. -->
```

### *Table*

표를 작성하기 위해 시작하는 태그로, 내부에 tr, th, td등 테이블을 구성하는 태그를 다수 포함하고 있다.

``` HTML
<!-- 3x2 표 작성 -->
<table>
    <tr> <!-- Header 위치, thead로 그룹 가능-->
        <th>제목1</th>
        <th>제목2</th> <!-- 제목, Column Header -->
    </tr>
    <tr><!-- Body 위치, tbody로 그룹 가능-->
        <td>내용1</td>
        <td>내용2</td> <!-- 내용 -->
    </tr>
    <tr><!-- 최하단, Foot 위치, tfoot로 그룹 가능-->
        <td>내용3</td>
        <td>내용4</td>
    </tr>
</table>
```

``` HTML
<!-- 그룹 하였을 때는, thead - tfoot - tbody 순으로 작성해야 한다. -->
<table>
    <thead>
        <tr>
            <th>제목1</th>
            <th>제목2</th> 
        </tr>
    </thead>
    
    <tfoot>
        <tr>
            <td>내용3</td>
            <td>내용4</td>
        </tr>
    </tfoot>
    
    <!-- thead와 tfoot은 표에 하나씩 존재할 수 있으므로 먼저 작성하고, 그후 tbody를 작성한다.-->
    <tbody>
        <tr>
            <td>내용1</td>
            <td>내용2</td> <!-- 내용 -->
        </tr>
    </tbody>
</table>

<!-- 행이나 열을 병합 할때는 th나 td 스타트 태그에 colspan, rowspan 속성을 사용하여 병합할 수 있다. -->
```
- JS의 Framework중에 thead, tfoot으로 작성하는 그룹핑이 필수인 것이 있어, 가능한 그룹핑을 하는것이 권장된다.

<br>

### *List*

순서가 있는 리스트 ol(Ordered List)와 없는 리스트 ul(Unordered List)

ol은 숫자로 글머리 기호가 생성되고, ul은 도형으로 글머리 기호가 생성된다.

``` HTML
<!-- ol -->
<ol>
    <li>1</li>
    <li>2</li>
    ...
</ol>

<ol start="3"> <!-- Ordered List의 시작 번호를 지정한다.-->
    <li>3</li>
    <li>4</li>
    ...
</ol>

<!-- ul -->
<ul>
    <li>-</li>
    <li>-</li>
    ...
</ul>
```

<br>

### *Semantic*

태그 이름이 의미 전달과 검색 성능 향상을 목적으로 하여 유의미한 이름으로 되어있음
> 이전버전들에서 div로써 작성되던 것을 정리한 것이라고 봐도 될 듯

- semantic : '의미를 갖는다'는 뜻으로, 각 태그가 스스로 의미를 지닌다는 뜻
- header : 사이트에 대한 소개 정보나 메인 메뉴, 사이트 로고 등이 포함됨
- nav : 사이트의 메뉴나 링크 같은 네비게이션 요소들이 포함
- section : 실제 문서 내용이 들어감
- article : 문서 내용이 많을 경우 여러 개의 \<article>요소로 나눌 수 있음
- aside : 문서의 주요 내용 외의 내용들을 넣어 문서의 주영역 주변에 배치
- footer : 작성자 정보나 저작권 정보, 또는 관련 문서 링크 등 부가 정보들을 담고 있음. 주로 문서 하단에 배치

<br>

### *Block, Inline*

Block level의 태그들은 브라우저에서 보여질 때, New Line(\N)을 생성하며, 전체 너비를 사용한다. 
- 대표적인 태그: div, p, ol, ul, li, table

Inline level의 태그들은 \N 없이 보여주며, 필요한 너비 만큼 사용한다.
- 대표적인 태그: a, span, img

<br>

### *div, span*

div : 다른 HTML 태그들을 그룹화하기 위한 컨테이너 역할, CSS와 같이 사용하여 레이아웃 및 태그 그룹핑 목적

span : Inline 속성을 가졌으며, Text를 위한 컨테이너 역할, width, height 속성 적용 불가

### *Form, 사용자가 Data를 입력할 수 있는 태그*

> input 태그의 종류와 그 속성들에 대해서는 [이곳](https://developer.mozilla.org/ko/docs/Web/HTML/Element/input)을 참조하는 것이 좋다.


\<form> 태그 내부에 전송 버튼인 \<input type="submit"> 이 있어야 서버로 전송이 된다.
- submit을 하게 되면 \<form> \</form> 내부 내용이 전부 전달된다.
- input type="submit" 대신 \<button> \</button>을 써도 가능하나, 오래된 html 버전에서는 지원하지 않을 가능성이 있다.
- \<input type="reset">은, 초기값, html이 불러와졌을 때의 상태로 되돌리는 동작을 한다.

``` HTML
<body>
    <form action="Path" method="GET|POST">
        <input type="Type">
        <input type="submit">
        <input type="reset">
    </form>
</body>
```
- action :  a 태그의 href같은 이동할 위치, 전달 대상 경로 지정. submit으로 특정한 데이터를 입력할 위치
- method : 전달 방식으로 값은 get과 post 두가지로 나뉜다.
    - GET : URL에 입력한 키와 값들이 포함되어 전송된다.
    - POST : 데이터는 전송되지만 URL에 포함되지 않는다.

form 요소들의 공통 속성들
- required(="required") : 필수값을 지정하는 옵션으로, 반드시 입력되어야 할 값에 사용된다.

- name= 은 key값을 설정하는 것으로, 특정 파라미터를 정해야 할 때 사용된다.
    - GET 방식으로 확인할 때, ?name=Value 형식의 주소가 나타난다. 이러한 형식이 서버에 전달된 파라미터 key, value 값을 의미한다. POST 방식으로는 확인 할 수 없다.
    
    - Query String이라고 부른다. 여러개의 key, value값이 전달된 다중 Query String일 때, &으로 연결한다. e.g., ?name=Value&age=23

    - key를 통하여 value를 얻을 수 있다. 
        > django 탬플릿 태그, {{}} 사용할 때도 종종 사용됨

type="text"

```HTML
<form>
    <input type="text" name="name" placeholder="Message" autofocus>
</form>
```

- 텍스트 한 줄을 입력하는데 사용되는 태그. 브라우저에는 Text box가 생성된다.
- placeholder : text box내에 흐릿하게 보이는 메시지로, 가이드 역할을 한다.
- autofocus : 여러개의 text box가 있을 때, 커서 위치를 잡아주는 속성

<br>

type="radio"

```HTML
<form>
    <input type="radio" name="Name" value="Value1" checked>Label
    <input type="radio" name="Name" value="Value2">Label
</form>
```

- 설문조사지에서 보이는, 단일 선택용으로 사용되는 태그. 브라우저는 선택 박스가 생성된다.
- 가능한 name을 동일하게 지정해야 한다.
- 내용을 입력할 수 있는 태그가 아니므로 value로써 넘어갈 value값을 주어야 한다.

- Label : HTML이 렌더링 되었을 때 보여질 값
- checked : 자동으로 선택되어 있는 값(Default)을 지정할 수 있다.

<br>

input type="checkbox"

```HTML
<form>
    <input type="checkbox" name="Name" value="Value1" checked>Label
    <input type="checkbox" name="Name" value="Value2">Label
</form>
```

-  radio가 단일이라면 checkbox는 다중 선택용이다. 같은 name이지만 여러개가 전송 될 수 있다.
- 체크된 값만 전송된다.
- checked(="checked")로 자동 선택되어 있는 값을 지정할 수 있다.

<br>

select name="", option value=""

```HTML
<form>
    <select name="Name">
        <option value="" selected>Label</option>
        <option value="Value1">Label</option>
        <option value="Value2">Label</option>
    </select>
</form>
```

- 드랍다운 목록을 통하여 선택하고 전송한다.
- switch-case 문에 가깝다.
- selected(="selected")로 우선 선택을 지정한다.

<br>

textarea

```HTML
<form>
    <textarea name="Name" rows="10" cols="30">Default Label
     </textarea>
</form>
```

- 여러줄 문자를 작성하고 전송하는데 사용된다.
- row와 cols를 통하여 화면에 표시될 텍스트 박스의 크기를 정할 수 있다.

<br>

input type="file"

```HTML
<form method="post", enctype="multipart/form-data">
    <input type="file" name="Name" id="theFile" multiple="multiple" accept="image/*" >
</form>
```

- 파일을 첨부할 수 있음, file upload

- accept=:"" 를 통하여 파일의 형식을 지정할 수 있음
- multiple="" 을 통하여 여러개의 파일을 선택할 수 있음
- method="post", enctype="multipart/form-data" : 파일 업로드시 필수 사항
    - 파일들은 Query String에 입력할 수 없기 때문에, POST 형식이 강제되고, RFC 1867 규약에 따라 form-data를 필요로 한다.

<br>

input type="email"

- 이메일 형식을 받을 수 있게 한다.
- 유효성 검증이 있어서 이메일 형식이 아니면, 에러가 발생한다.

input type="search"

- clear 기능이 추가되어 있는 text 형식이다.

input type="color"

- 색을 입력할 수 있으며, JS와 연동하여 값을 받아올 수 있다.

input type="hidden"

- 존재하는 값이지만, 사용자가 별도로 값을 입력할 수는 없는 상태가 된다.
- 인증키같은, 유저한테 알리지 않고 자동으로 전송되어야 하는 값에 사용

<br>

Custom data, HTML5 문법

``` HTML
<a href="" data-width="900" data-height="400" ...>
```

- 대부분의 속성은 tag에 종속적이라 없는 속성을 사용했을 때 유효성 검사에서 문제가 될 수 있다.

- custom data는 data- 접두어로 작성하며, 유효성 검사기는 이 접두어로 시작되는 속성은 무시한다. 
- 사용 불가능한 속성이나 임의의 속성명을 주석처럼 작성 할 수 있다.

### *Image*

``` HTML
<img src="images/main.png" alt="main 이미지" 
     width="200" height="200"><br>
```
- src : 이미지 불러오기, 소스 파일, 경로지정
- alt : 이미지 파일이 없을 때 출력될 메시지
- width = 이미지의 폭
- height = 이미지의 높이

<br>

### *특수 문자*
다중 공백을 인식하지 못하고, <>는 tag의 문법이라 부등호로써 사용할 수 없다.
따라서 이를 해결하기 위해 특수 문자를 사용한다.
```HTML
<p>3&lt;4</p> <!-- 부등호 <-->
<p>30&gt;4</p> <!-- 부등호 > -->
<p>&quot;홍길동&quot;</p> <!-- 쌍따옴표 " -->
<p>이순신&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;유관순</p> <!-- 공백, 자주 쓰인다.-->
```

<br>

### *경로 지정 방식*

절대 경로와 상대 경로 두가지 방법이 있다.

``` HTML
<!-- 현재 html의 주소 : localhost:port/Pfolder/Cfolder/AAA.html -->
<!-- 필요한 이미지의 주소 : localhost:port/Pfolder/Ifolder/image.jpg -->
<body>
    <img src="/Pfolder/Ifolder/image.jpg"> <!-- 절대 경로 방식 -->
    <img src="../Ifolder/image.jpg"> <!-- 상대 경로 방식 -->
</body>
```

- 절대 경로 : / 시작, localhost:port(127.0.0.1:Port)부터 시작하는 것이 절대 경로
    - 사용은 쉬우나, 수정이 어렵다

- 상대 경로 : 현재 html 파일이 존재하는 directory가 기준이 되어 경로가 검색됨
    - . : 현재 directory, .. : 부모 directory
    - 사용하는데 직관적이지 않지만, 수정이 비교적 용이하다.

##### Memo
html5    
tag종류    
dom, domtree    
form : action, method    
input type submit, button, input type button    
Path : Abs Path, Rel Path    
