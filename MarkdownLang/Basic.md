# **Markdown?**

텍스트 기반의 마크업 언어(Markup Language)로, 쉽게 쓰고 읽을 수 있는 문서 양식을 지향한다. 특수기호와 문자를 이용한 매우 간단한 구조의 문법을 사용하여 웹에서도 보다 빠르게 컨텐츠를 작성하고, 직관적인 인식이 가능하다.

> Markup Language, 태그를 활용하여 문서나 데이터의 구조를 명시하는 언어

---
## **Syntax**
[Guide Site](https://www.markdownguide.org/ "markdown guide")

---
### **Header**


제목이나 글머리를 작성하는데 사용

```
#   Heading level 1
##   Heading level 2
###   Heading level 3
####   Heading level 4
#####   Heading level 5
######   Heading level 6

- Alternate lv1, 2

Heading Level 1
===============

Heading Level 2
---------------
```

---
### **Blockquotes**
인용문
```
> Quotes Contents
```
> Quotes Contents

#### **Nested Blockquotes**
중첩 인용문
```
> First Quotes
>> Second Quotes
```
> First Quotes
>> Second Quotes

---
### **List**
순서가 있는 리스트(Ordered List; ol)과 순서가 없는 리스트(Unordered List; ul)

#### **Ordered List**
내용 앞에 숫자와 . 을 사용하여 순서를 나타낸다

```
1. First
    1. Indented
2. Second
3. Third
```
1. First
    1. Indented  
2. Second
3. Third


#### **Unordered List**
내용 앞에 글머리 기호 `*`, `+`, `-` 등을 사용하여 나타낸다

글머리 기호는 혼용도 가능하다.

```
* 1단계
    + 2단계
        - 3단계
```
* 1단계
    + 2단계
        - 3단계

---
### **Code Block**
코드를 작성할 때 사용하는 블럭

`` ``` ``,  Backtick 기호를 세번 연달아 사용하여 작성

첫 코드 블록 기호 옆에 사용하는 언어 기재하면, 그 언어의 문법대로 표현
``` 
    ``` python
    for i in range(len(list)):
        tmp_list = list[i]*2
    print(tmp_list)
    ```
```
``` python
    for i in range(len(list)):
        tmp_list = list[i]*2
    print(tmp_list)
```

---
### **Code**
인라인(Inline)이라고도 불리는 것으로 글자를 `` ` ``으로 감싸 사용한다.
```
`Java`, `Python`
```
`Java`, `Python`

---
### **Link**
링크 생성
```
[구글 링크](https://www.google.com/)
```
[구글 링크](https://www.google.com/)

---
### **Image**
이미지를 추가   
인터넷 경로나 폴더 경로등을 사용

```
![Image](https://upload.wikimedia.org/wikipedia/commons/2/28/HelloWorld.svg)
```
![Image](https://upload.wikimedia.org/wikipedia/commons/2/28/HelloWorld.svg)

---
### **Emphasis**
볼드(Bold)나 이탤릭(Italic)등, 문장이나 단어를 강조

#### **Bold, 굵게**
``` 
**Target** 
```
**Target** 

#### **Italic, 기울임**
``` 
*Target*
```
*Target*

#### **Strikeout, 취소선**
``` 
~~Target~~
```
~~Target~~ 