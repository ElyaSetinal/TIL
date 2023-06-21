## **Design, layout**

### *크기 단위*

width, height, margin, padding 등 CSS에서 크기나 간격 등을 설정하는데 사용하는 길이 단위.

절대값에선 px(pixel)를 많이 쓰고, 상대값에선 em(element), rem(root element)으로 많이 쓴다.
- 사이즈를 지정하지 않았을 때, 기본적으로 16px의 사이즈를 가진다. (1rem = 16px = 1em)

[참조](https://www.w3schools.com/cssref/css_units.asp)

em은 부모 노드의 크기 정보를 받아서 그것을 기준으로 계산한다.
- 중첩 구조의 경우는 예상치 못하게 크기가 달라질 수 있으므로, 가능한 rem을 사용한다.

<br>

### *색상*

color

요소의 색상을 결정하는 속성

- 영단어, 120가지 속성으로 정해진 색상 값을 가진다.
- 16진수, #00FFFF 같이 6자리의 코드로도 가능하고, #0F0의 RGB 코드로도 가능하다.
- 10진수, RGBA로 표기하며, A는 투명도를 의미한다. rgba(255, 255, 255, 0.5):검정색 투명도 50%


### *표시 방식*

display 속성 - 영역 표현 방식을 지정하는 속성
- inline : block 속성을 inline으로 변경할 때
    - Navigation Bar를 작성할 때 주로 사용 (상단 메뉴가 보통 가로로 되어 있음)
- block : inline 속성을 block으로 변경할 때
- None : 표시하지 않을 때. 다만 영역 유지가 되지 않아 사라지는 것과 동일하게 표현된다.
- inline-block : inline 속성이 되지만, width나 height처럼 크기를 설정하는 속성을 사용 가능하다.

visibility 속성 - display와 동일한 표시에 대한 속성이지만, 영역은 유지가 된다.
- JS와 연동하여 동적인 표현이 가능하게 하는 속성중 하나
- visible : default값
- hidden : display: None 처럼 안보이게 하지만, 해당 영역이 유지가 되어 빈 공간으로 나온다.
- collapse : Table을 보이지 않게 만들면서 동시에 영역도 같이 제거한다.

opacity 속성
- 요소의 투명도를 지정하는 속성으로, color의 alpha와 비슷한 역할을 한다.

<br>

### *Box 모델, Content Box*

레이아웃을 구성할 때 중요한 개념으로, block, lnline 상관없이 모든 tag는 box로 구성되어 있다.

- width, 내용에 대한 속성으로, 너비(폭)-가로 길이를 의미
- height, 내용에 대한 속성으로, 높이-세로 길이를 의미

> width와 height는 명시하지 않으면, width는 화면 전체, height는 내용의 높이 만큼 할당한다. 즉, 이미지 크기가 800x600 일 때 지정하지 않으면 800x600만큼 박스가 생성된다.

- border, 박스에 대한 속성으로, 테두리를 의미한다. 상하좌우 두께의 속성값이 존재한다.
    - width(두께), style(선 스타일), color(선 색상) 3가지 속성이 존재한다.
    - border: Width Style Color 순으로 한번에 작성이 가능하다.
    - border-radius : 테두리의 모서리를 곡선으로 변경, px에 따라서 얼마나 둥글어 지는지 결정

- padding, 여백에 대한 속성으로, 테두리와 내용 사이의 안쪽 여백을 의미한다. 내용을 기준으로 상하좌우 속성값이 존재한다.

- margin, 바깥 여백에 대한 속성으로, 하나의 박스와 다른 박스간의 바깥 여백을 의미한다. padding과 동일하게 상하좌우 속성이 존재한다.
    - margin:auto : 화면 너비와 관련없이 중앙 정렬

- Content Box를 가지고 레이아웃을 구성할 때, 내용에 대한 속성뿐만 아니라, 여백과 테두리에 대한 속성도 고려 해야 한다.

    - 전체 너비 : width + L_Padding + R_Padding + L_Border + R_Border + L_Margin + R_Margin
        - 내용 너비 + 좌우 안쪽 여백 + 좌우 테두리 두께 + 좌우 바깥 여백

    - 전체 높이 : height + T_Padding + B_Padding + T_Border + B_Border + T_Margin + B_Margin
        - 내용 높이 + 상하 안쪽 여백 + 상하 테두리 두께 + 상하 바깥 여백

<br>

### *Box 모델, Border-box*

Content box는 각 속성들을 전부 계산하여 레이아웃을 구성해야하는 귀찮음이 존재한다.

이를 해결하기 위해 border-box라는 속성을 이용, 전체 박스 크기를 유지한다.

box-sizing: border-box, width와 height를 지정하면 이 크기에 padding, border의 크기가 포함되어 박스가 구성된다. 최외곽을 고정하여 크기를 설정한다.
- 즉, 여기서는 width나 height가 내용에 대한 값이 아니라, 전체 크기에 대한 값이라고 생각하자.
- Margin은 border-box 형식이라도 별도로 계산된다.

<br>

### *Background*
html 페이지의 배경을 설정
[참조 사이트](https://www.w3schools.com/cssref/css3_pr_background.php)

- background-image:url(~~) : 이미지의 주소를 넣음으로써, 해당 이미지로 배경을 설정
- background-attachment : 배경을 고정할것인지, 스크롤따라 움직일 것인지
    - attachment, 부착 >> 화면에 붙일 것인지(스크롤해도 유지), 배경에 붙일 것인지(스크롤 같이 움직임)
- background-position : HTML의 전체 크기 기준으로 위치
- background-color : 전체적인 배경 색상 설정

<br>

### *Font*
> 사용자의 컴퓨터, 브라우저에 폰트가 없으면 폰트가 적용되지 않는다.<br>
따라서 여러개의 폰트(Font Family)를 지정해두고, 마지막에 Generic Family 를 적어서 사용한다.

generic family, 폰트 그룹
- sans-serif : 글 꼬리가 없음
- serif : 글 꼬리가 있음

font family, 실제 폰트 이름
- Arial, Times, Georgia, 맑은 고딕, 나눔 고딕, 바탕, 명조 등

> Generic family는 최후의 보루, 앞에 지정해둔게 다 없으면 이거라도 써라 라는 의미


Font size
- 기본은 16px
- 특정한 px 값이나 em을 통해 지정할 수도 있고, rem등 상대 길이를 사용할 수 있으며, xx-small 부터 xx-large까지 7단계로 지정된 값을 사용할 수 도 있다.

Font Style
- 기울임(Italic)

Font weight
- 폰트의 두께, bold가 여기에 포함된다.

`font: Style Weight Size Family` 순으로 작성함으로써 한 줄에 작성이 가능하다.

```CSS
font: italic bold 1rem Arial, Gerogia, Times, serif;
```

Font Face
직접 폰트를 제공할 때 사용
\<head>, \<style>에 내부에 작성하여 제공할 수 있다.

- 폰트에도 라이센스가 있기 때문에, 라이센스를 확인하고 사용해야 한다.

<br>

### *Text*
정렬, 변경, 들여쓰기, 단어/글자 간격, 취소선 등 텍스트에 대한 각종 속성들을 의미한다.

- text-color  : 글자의 색상
- text-align  : 글자를 정렬, 중앙정렬이나 끝맞춤이 여기에 들어간다.
- text-decoration : 밑줄, 윗줄등 줄에 대해서 지정 및 해제 하는 속성
- text-indent  : 첫 라인의 들여쓰기 크기를 설정

<br>

### *position*

top, bottom, left, right 4가지 속성과 함께 사용이 된다.

Static : 기본인 normal position, 고정된 속성으로 추가적인 position 속성이 적용되지 않는다.
Relative : normal position인 위치를 기준으로하여, 상대적인 위치로 이동한다.
Absolute : Relative인 부모 tag의 박스를 기준으로 하여, 그 내부에서 어디에 위치 할 것인지를 지정
fixed : 브라우저 화면(Viewport, PC/Mobile 등)을 기준으로 하여, 고정된 위치를 지정

<br>

### *z-index*
요소의 stack 순서를 변경하는데 사용. 

최초 작성요소가 0부터 시작한다. -1을 주면 최하단에 작성

> 여러장의 종이(요소)가 쌓여있다고 생각하면, 가장 밑에 있는 종이를 z-index: 0 이라고 생각하자

<br>

### *float*

레이아웃 작성시에 사용하는 속성으로, '띄우기'라는 의미가 있다.

float를 적용하면 지정된 위치에 box 사이즈에 맞추어 작성을 하고, 나머지 공간에 그 다음 box를 놓는다.
- 워드 문서들에 이미지를 넣고, 텍스트 줄 바꿈 옵션을 넣는 느낌

상위 div에 float가 있으면, 하위 div에는 float가 별도로 지정되지 않아도 작동한다.(종속성)

상위 모든 box들이 float가 되면, 그 다음 box는 float된 box 하단으로 들어간다.
- 원하지 않는 float를 지우기 위해 clear 속성을 사용한다.
    > 상위 div들이 모두 float가 되면, 하위 div는 원하지 않아도 float된 div들 밑으로 들어가게 된다.(안보이게 됨)
- float와 clear를 동시에 사용하는 것 보다는, float되는 요소끼리 wrapping 하는것이 좋다.

[참조 사이트, w3school](https://www.w3schools.com/css/css_float.asp)

<br>

### *Flex box*
item이 배치/나열 되어 있을 때, flex container를 생성하는 지정 방법. 계층 구조 지정이 편하여 다양한 레이아웃을 만드는데 사용된다.

- 위에 작성된 float 속성을 대체하기에 매우 적합한 방식으로, 별도의 float 지정이 없어서 동일한 레이아웃을 구축할 수 있다.
- flex container에서는 CSS로 display:flex를 반드시 지정해야 한다.
- conatiner는 item으로써 역할을 할 수 있다. (중첩 Container)
- container 내부의 요소들은 flex item이라 불린다.

#### *Container 속성들*
> container 단계에서 적용한 속성은 자손에서 적용되지 않기에, 자손에도 어떤 속성이 필요하다면 자식 단계에서 재 지정해야 한다.

각 속성들의 제목에 MDN 링크가 추가되어 있으니, 데모 및 자세한 사항에 대해선 링크 참조

[flex-direction](https://developer.mozilla.org/ko/docs/Web/CSS/flex-direction)

Default Main Axis는 Row이고, 90도로 교차되는 축(Column)을 교차축(Cross Axis)이라 부른다.
- 배치 방향을 지정하는 옵션으로 row, row-reverse, column, column-reverse 가 사용된다.
    - row-reverse는 기본 방향인 좌 > 우가 아니라 우 > 좌 순으로 배치한다. e.g., 123 > 321

[flex-wrap](https://developer.mozilla.org/ko/docs/Web/CSS/flex-wrap)

기본적으로 flex item은 한줄에 보이기 위해 자체 축소를 하면서 줄바꿈이 되지 않는다.

wrap 속성을 적용하면 item 자체의 크기를 유지시키고 교차축으로 이동하는데 사용되는 기능이다. 
- viewport에 따라서 다르게 보여야 하는 반응형 웹에 자주 사용되는 속성
- wrap 속성을 적용하면 내용 Container의 크기가 유지되어야 하기 때문에, Cross Axis 방향으로 줄바꿈을 한다.

[flex-flow](https://developer.mozilla.org/ko/docs/Web/CSS/flex-flow)

direction과 wrap 속성을 한번에 모두 설정하기 위한 단축 표현. 설정되지 않은 값은 기본값으로 사용

[justify-content](https://developer.mozilla.org/ko/docs/Web/CSS/justify-content)

주 축(기본 Row)에 대한 정렬을 설정하는 속성
- start, center, end, space-around, space-between, space-evenly
    - space-around : 양 끝 여백은 항목 사이 간격의 절반만큼 간격을 갖도록 배치
    - space-between : 첫 항목과 마지막 항목은 각 끝부분에 밀착되고, 나머지는 사이 간격이 일정하도록 배치
    - space-evenly : 모든 항목이 서로간에 동일한 여백을 갖도록 배치

[align-items](https://developer.mozilla.org/en-US/docs/Web/CSS/align-items)

교차 축(기본 Column)에 대한 정렬 설정
- start, end, center, stretch, baseline

[align-content](https://developer.mozilla.org/ko/docs/Web/CSS/align-content)

wrap이 적용된 항목에만 적용 가능하며, wrap이 된 그룹끼리 교차 축에 정렬되는 방식을 제어
- justify-content나 align-items이 요소에 대한 속성이라면, align-content는 그룹, wrap에 대한 속성이다.
- flex item들이 한 줄로 구성된다면 영향이 없다.
- start, center, end, space-between, space-around, strectch

<br>

#### *item 속성*

[order](https://developer.mozilla.org/ko/docs/Web/CSS/order)

요소가 배치되는 순서를 설정, 변경할 수 있는 속성
- 기본값은 0이고, order값이 작은 순서대로 표시된다.

[flex-basis](https://developer.mozilla.org/ko/docs/Web/CSS/flex-basis)

기본적으로 컨텐츠의 크기만큼의 길이를 가지는 item의 초기 길이(Default:auto)를 설정
- 보통 수치를 작성할 때, 크기 단위(px, rem, em 등)을 같이 작성한다.
- width 속성을 사용해도 상관은 없으나, basis는 이후 작성될 몇몇 속성의 기준 길이로써 동작한다.
- width와 basis를 동시에 값을 지정할 때는 basis 값을 따라간다. 단, min/max-width는 width를 따라간다.

[flex-grow](https://developer.mozilla.org/ko/docs/Web/CSS/flex-grow)

여분 공간이 있을 때, 아이템이 얼마나 확장 될 것인지를 설정하는 속성
- basis를 기준 길이로 사용하고 별도로 지정하지 않으면 빈 공간을 유지한다.(기본값 0)
- 비율에 대한 설정으로, 여러 요소가 grow 속성을 가지면 비율대로 확장한다.(grow가 크면 크게 확장)

[flex-shrink](https://developer.mozilla.org/ko/docs/Web/CSS/flex-shrink)

grow와 반대로, 공간이 부족할 때 얼마나 축소 될 것인지를 설정하는 속성
- 기본값이 1이라서, 모두 균등하게 축소된다. 0으로 설정하면 축소되지 않는다.
- 역시나 비율에 대한 설정이라서, 여러 요소가 값을 가지면 비율대로 축소한다(shrink가 클수록 크게 축소)

[flex](https://developer.mozilla.org/ko/docs/Web/CSS/flex)

grow,shrink,basis 세가지 속성을 한번에 설정하기 위한 표현 방식
- 기본적인 순서는 grow shrink basis를 갖는다
    - 단순 숫자만(unitless) 있다면 grow-shrink 속성 순으로 입력되고, 크기 단위가 같이 있으면 basis로 입력된다.
    ``` CSS
    S{flex: 2 2 10%}; /* Three values: flex-grow | flex-shrink | flex-basis */
    S{flex: 1 30px}; /* Two values: flex-grow | flex-basis */
    S{flex: 2}; /* One value, unitless number: flex-grow */
    S{flex: 10em}; /* One value, length or percentage: flex-basis */
    ```

[align-self](https://developer.mozilla.org/en-US/docs/Web/CSS/align-self)

align-items는 container에서 지정하는 속성이기 때문에, 모든 items에 적용된다. 개별적으로 재정의 하기위하여 align-self 속성을 사용한다.

<br>

### *Media Queries*
여러 미디어 유형에 대하여 스타일 규칙을 사용함
viewport의 너비나 높이, 방향등의 정보를 활용하여 반응형 app을 구현하는데 사용된다.

``` CSS
@media MediaType and (표현식) {
    CSS_Code
}
```

- MediaType에는 all, print, screen등이 있으나, Screen이 제일 많이 사용된다.