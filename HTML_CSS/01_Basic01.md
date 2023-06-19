## Web application architecture, 웹 사이트

클라이언트 <> 서버(Web Server; apache, Ngix)

서버에 HTML(HyperText Markup Language)을 작성하여 이를 정적 서버(Apache, Ngix등)에 저장 - 클라이언트가 URL로 요청 -  요청한 html 검색(200 or 404 등) - 요청한 html 반환(응답) - 반환된 html 로컬에 저장 - 렌더링(표시)

- CSS나 JS등은 Client-Side Programming, 클라이언트 측에서 실행된다.
- html은 정적(Static)한 특성을 갖는다. 클라이언트와 관계 없이 같은 값, 같은 표현을 갖는다.

<br>

### Container
'검색'만 가능한 HTML, CSS, JS와 다르게 클라이언트가 요청을 하고, 내부적으로 처리한 다음 그 결과를 html로서 반환하는 것을 동적 파일 처리라 부른다.

이러한 동적 파일을 처리하는데 쓰이는 서버가 동적 서버, Container라고도 부른다.

이러한 동적 파일 처리를 구축하고 서버에서 동작하는 Framework에는 python에 django, Java에 jsp/servlet, MS계열의 C#, ASP, PHP 등이 있다.

일반적으로 서버는 정적 처리와 동적 처리를 같이하고, 이를 보통 WAS(Web Application Server)라 부른다.

<br>

### URL Format

http(s):// 서버 ip(Apache, Ngix등의 서버):Port 번호/자원(보고자 하는 파일명)

- 서버ip와 포트를 숨기고 싶거나, 너무 어려워서 쉽게 접근하게 하고 싶을 때, 도메인을 사용한다. 보통 도메인 제공자가 따로 있어서 요청해야 한다.

- 자원이 없는 경우 404 not found, http 상태 코드가 나온다.
- 있는 경우, 200 상태 코드가 서버상에 출력되고, 자원을 반환

[상태코드 목록 - 모질라 재단](https://developer.mozilla.org/ko/docs/Web/HTTP/Status)

<br>

### Web Standard
특정 기기와 상관없이 정보에 접근 가능해야 함
- 데이터 구조 HTML + 디자인/레이아웃 CSS + 동작 및 컨트롤은 JS와 DOM(python에선 django)이 담당해야 한다.

다양한 브라우저, 환경에서 동일한 결과를 내기 위하여, 중구난방으로 작성되어 있던 html, js등을 표준화 하여 HTML5, ECMAScript6 라는 표준이 등장함

<br>

### HTML
- HyperText Markup Language, 링크가 가능한 \<tag> 구성 언어

\<tag>(시작 태그) Body(몸체) \</tag>(종료 태그, 없는 경우도 있음)

- body에는 html에서 표시할 값들이나, \<tag> 를 다시 사용하여 중첩 형태를 작성 할 수 있다.

- 시작 \<tag>에는 여러가지 Key="Value" 형태의 값을 넣을 수 있는데, 이를 속성명-속성값이라고 부른다.
    - key들은 전역적으로 사용할 수 있는 것이 있고, 특정 태그에 종속되어 있는 것도 있다.

- empty tag, Body가 없는 tag로써, \<tag/> 로 표현된다.

<br>

### HTML5의 기본 문법

``` HTML
<!DOCTYPE html> <!--html의 버전 표시-->
<!-- HTML의 주석 표시 방법 -->
<html>
    <head>
        <title>Title등 작성</title>
    </head>
    <body>
        <h2>렌더링할 내용, 링크등 실제 내용을 작성</h2>
        <p>DOM(Document Object Model) 작성</p>
        <a href="aLink">Link</a>
        <!--DOM : HTML 문서에 있는 태그에 해당되는 객체를 생성하고 Tree로 만드는 구조-->
    </body>
</html>
```


#### DOM Tree
Document Object Model, 객체 지향 모델로써 구조화된 문서를 표현하는 방식

HTML, XML 문서의 프로그래밍 인터페이스이고, 이 DOM 구조를 통하여 문서의 내용(값이나 속성)을 조작하고 제어할 수 있으며, 이러한 DOM을 Tree 형태로 표현한 것이 DOM Tree이다.

```
html
└ head
  └ title
    └ "Title"
└ body
  └ h2
    └ "렌더링할 내용 ..."
  └ p
    └ "DOM ..."
  └ a      - href        # 태그 노드 - 속성 노드
    └"Link"  └ "aLink"   # 값 노드
```

태그, 속성명, 값들을 총칭하여 노드(Node)라 부른다.
- 태그 노드, 엘리멘트 노드(Element Node)
- 값 노드, 텍스트 노드(Text Node)
- 속성 노드, 어트리뷰터 노드(Attribute Node)
    - 속성 노드는 태그 노드의 

> - Root Node : 최상위 노드(html)    
> - 부모 노드 : 한 단계 위 레벨의 연결 노드(head 기준 html)
> - 자식 노드 : 한 단계 아래 레벨의 연결 노드(head 기준 title)
> - 조상 노드 : 두 단계 이상 위 레벨의 연결 노드(h2 기존 html)
> - 자손 노드 : 두 단계 이상 아래 레벨의 연결 노드(html 기준 h2)
> - 형제 노드 : 같은 부모 노드를 가진 같은 레벨의 노드(h2, p, a)
