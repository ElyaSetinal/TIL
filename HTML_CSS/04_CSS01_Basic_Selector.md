## **CSS, Cascading Style Sheets**

- CSS는 표현을 담당하는 언어
- 요소가 어떻게 렌더링 되고, 실제로 어떻게 보일지를 기술하는 스타일 언어이다.
- Cascading : 폭포라는 의미가 있고, 상속 또는 종속이라는 의미가 있다. 부모 태그에서 스타일을 정의했더라도, 자식 태그에서 스타일을 **재정의**가 가능하다
- DOM Tree를 작성하면, CSS의 내용이나 적용 범위를 확인하기 편하다.

<br>

### *기본 문법*

선택자와 선언 부분으로 구성

``` CSS
선택자(Selector) { /* 선택자(Selector) : DOM Tree에서 Node를 선택하는 방법 */
    속성(Attribute):속성값(Value) /* 선언, 속성은 Property라고도 불린다. */
    ...
}
```

- Inline 방식

    ``` HTML
    <p style="Attribute:Value;"></p>
    ```

    - 스타트 태그에 style 속성을 사용하여 작성
    - 간단하나 모든 태그마다 지정해야하는 단점이 있다.
    - CSS 적용해야 할 요소가 소수일 때 적합


- Internal 방식
    ``` HTML
    <head>
        <style>
            selector {
                Attribute:Value;
            }
        </style>
    ```
    - \<head>에 \<style>을 사용, CSS를 작성하여 적용하는 방법

- External 방식
    ``` CSS
    selector {
        Attribute:Value;
    }
    ```

    ``` HTML
    <head>
        <link rel="stylesheet" type="text/css" href="css/external.css">
    </head>
    ```
    
    - \<head>에서 \<link>를 통하여 외부 CSS를 연결하여 사용
    - CSS 적용해야 할 부분이 많을 때 사용하면 좋다.

<br>

### *선택자 방식 - tag, id, class*

Internal, External 방식에서처럼 특정 선택자를 지정하는 경우에 사용할 수 있다.(여기서는 internal 방식, p tag 선택자로 설명한다.)

tag, 직접 적용할 tag를 CSS에 적용하는 방식

``` HTML
<head>
    <style>
        p {
            Attribute:Value;
        }
    </style>
</head>

<body>
    <p> </p>
</body>
```

- 직관적이고 쉽지만, 같은 태그지만 다른 스타일을 주어야할 때는 사용이 어렵다.
- 여러개의 태그에 같은 스타일을 주고 싶다면, 선택자를 여러개 작성하면 된다. (p, a, ...)

<br>

id, 가능한 고유의 별칭을 부여하여 접근

``` HTML
<head>
    <style>
        #AAA {
            Attribute:Value;
        }
    </style>
</head>

<body>
    <p id="AAA"> </p>
</body>
```

- \#AAA처럼 사용할 선택자 앞에 \#을 붙여서 접근한다.
- id는 가능한 유일한 값을 지정한다.

<br>

class, 중복 가능한 id

``` HTML
<head>
    <style>
        .AAA {
            Attribute:Value;
        }
    </style>
</head>

<body>
    <p class="AAA"> </p>
</body>
```

- \.AAA 처럼 . 을 사용하여 접근한다.
- 여러 태그에 중복되어 사용할 수 있으며, 중복되는 모든 태그에 같은 스타일을 적용한다.

<br>

## **DOM Tree 기반 선택 방식**

### *자손 선택자*

DOM 트리상 자손 노드를 선택하여 CSS를 적용함

``` CSS
Selector1  Selector2 { }
```

- 공백을 사용하여 자손 선택자에 CSS를 적용한다.
- Selector1은 검색의 기준점으로, CSS의 적용을 받지 않는다.
- 자식을 포함한다.

<br>

### *자식 선택자*

DOM 트리상 자식 노드를 선택하여 CSS를 적용함

``` CSS
Selector1 > Selector2 { }
```

- \> 기호를 사용하여 자식 선택자에 CSS를 적용한다.

<br>

### *형제 선택자*

DOM 트리상 형제 노드에 CSS를 적용함

``` CSS
Selector1 + Selector2 { }
```

- Selector1의 형제 노드인 Selector2에 CSS를 적용한다.
- +를 사용하면 단일 형제 노드에 적용
    - Selector2를 가진 태그나 클래스등이 여러개 있어도, 가장 먼저 나온 선택자에 적용된다.

``` CSS
Selector1 ~ Selector2 { }
```

- +와 동일한 기능을 하나, ~ 를 사용하여 모든 형제 노드에 적용
    - Selector2를 가진 모든 선택자에 CSS를 적용한다.

<br>

### *선택자-속성(Attribute)*

[] 를 사용한다.

``` CSS
[Attribute] { } /* 해당되는 모든 속성명에 CSS를 적용 */
Selector[Attribute] { } /* 해당되는 선택자+속성명이 일치 할 때 CSS를 적용 */
Selector[Attribute=Value] { } /* 해당되는 선택자+속성명+값이 일치 할 때 CSS를 적용 */
```

특정한 문자열을 가진 요소를 선택할 때 특수문자를 추가한다.

``` CSS
Selector[Attribute^=Value] { } /* Value로 시작하는 값을 확인하여 CSS 적용 */
Selector[Attribute$=Value] { } /* Value로 끝나는 값을 확인하여 CSS 적용*/
Selector[Attribute*=*Value] { } /* Value를 포함하는 값을 확인하여 CSS 적용 */
```

<br>

### *의사 코드(Pseudo Code)*

값 자체에 의미가 있는 코드

:코드, :으로 시작되는 코드 형식이다. 

[참조 사이트 : W3 School, CSS Selector](https://www.w3schools.com/cssref/css_selectors.asp)

``` CSS
selector:Pseudocode { }
```

selector:focus, 포커스(커서 위치)가 되어있는 곳에 CSS를 적용한다.

selector:first-child, 선택자의 부모를 기준으로, 첫번째 자식 노드인 해당 선택자에 CSS를 적용    
selector:last-child, 선택자의 부모를 기준으로, 마지막 자식 노드인 해당 선택자에 CSS를 적용    
selector:only-child, 선택자의 부모를 기준으로, 자식 노드가 해당 선택자 하나일 때 CSS를 적용    
selector:nth-child(n), 선택자의 부모를 기준으로, 자식 노드가 n번째이면서 해당 선택자일 때 CSS를 적용    
selector:nth-child(even), 선택자의 부모를 기준으로, 자식 노드가 짝수 번째이면서 해당 선택자일 때 CSS를 적용    
selector:nth-child(odd), 선택자의 부모를 기준으로, 자식 노드가 홀수 번째이면서 해당 선택자일 때 CSS를 적용    
selector:not(nth-child(n)), 선택자의 부모를 기준으로, 자식 노드가 n번째가 아니면서 해당 선택자일 때 CSS를 적용

selector:disabled, 해당 선택자이면서 disabled 속성이 있을 때 CSS를 적용    
selector:enabled, 해당 선택자이면서 enabled 속성이 있을 때 CSS를 적용    
selector:checked, 해당 선택자이면서 checked 속성이 있을 때 CSS를 적용, 자주 사용 됨    
- 보통 type=checkbox에 쓰이는데, 기존에 checked가 없어도 사용자가 선택해도 CSS가 적용된다.   

selector:empty, 해당 선택자이면서 Body가 없을 때 CSS를 적용

<br>

