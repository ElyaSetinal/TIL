## head 태그

### Link
문서에서 사용하는 외부 파일 경로를 지정할 때 사용된다.
주로 외부 CSS나 favicon등을 지정할 때 사용

``` HTML
<head>
    <link rel="Attribution" type="Media Type" href="Path">
</head>
```

- rel : 필수 속성으로, 현재 문서와 외부 리소스 사이 연관 관계 명시
- type : 외부 리소스의 타입 명시
- href : 외부 리소스의 위치 명시

<br>

### Style
HTML 문서의 스타일 정보 지정. 주로 내부 CSS 파일 지정시 사용

HTML에서 3가지 방식으로 사용이 가능하다.

- 인라인(Inline) 방식 : 시작 \<tag>에 style 속성을 이용한다.

``` HTML
<p style="Color:red">Hello</p>
```

- Internal 방식 : Head 태그 안에 \<style> 태그를 사용하여 작성

``` HTML
<head>
    <style type="text/css">
        p {
            CSS infor.
        } <!-- p tag의 CSS -->
        a {
            CSS infor.
        } <!-- a tag의 CSS -->
    </style>
</head>
```

- External 방식 : 외부 파일(.css)로 작성하고 연결하여 사용

``` HTML
<head>
    <link rel="stylesheet" type="text/css" href="mystyle.css">
</head>
```

- 링크를 걸고 작성할 때, href로 작성하는 파일의 경로를 주의 해야 한다. 기본 검색 위치는 상대 경로 = HTML이 존재하는 경로이다.

<br>

### JS

자바스크립트 명시에 사용하는 태그로, 주로 동작이나 제어를 나타내는데 사용된다.

- Internal 방식 : head 태그 안에 \<script> 태그를 사용하여 작성

``` HTML
<head>
    <script>
        ~~~ // JS 작성
    </script>
</head>
```

- External 방식 : 외부 파일(.js)로 작성하고 연결하여 사용

``` HTML
<head>
    <script src="AAA.js"></script>
</head>
```

- 혼합

``` HTML
<head>
    <script src="AAA.js"></script>
    <script>
        ~~~ // JS 작성
    </script>
</head>
```