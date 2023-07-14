## **제어문01, Control Statement01 : 조건문**

> 제어문이란 : 프로그램 흐름을 제어하는 경우에 사용 되는 실행문

## **조건문, Conditional Statement**
조건문 : 조건에 따라 동작하는 문장이 달라지게 하는, 분기를 만들 때 주로 사용
- if, if-else, if-elif-else

조건을 판별해야 하므로 boolean값이 반환되는 조건식이 들어가는데, 이때 사용되는 연산자로 비교 연산자, 논리 연산자, 멤버쉽 연산자 등이 사용된다.

> False로 취급되는 0, [], (), {}, set(), None 도 사용 가능

<br>

### *If*

``` py
if Conditional_Expression:
    Statement1  # 조건식(Conditional_Expression)이 True이면 동작

#e.g.
if (1+1)==2:  # It's True
    print("It's True")
```

가장 간단한 조건문으로, if와 같이 사용되는 조건문이 참(True)일 때 내부의 문장(Statement1)이 실행되는 형태이다.

> C나 Java에서는 이러한 문장을 작성할 때 {}, 중괄호로써 if 내부의 문장이 무엇인지 구분지었으나, Python에서는 이러한 구분자는 없고, 들여쓰기로써 문장을 구분한다.<br>
<br> - 들여쓰는 공백의 수는 정해져 있지 않으나, 파이썬 코딩 스타일 가이드인 PEP8 에서는 공백 4칸(일반적으로 Tab 1번)을 권장한다.<br> - 들여쓰기의 레벨(공백의 수)이 같아야 한다. 윗문장이 공백 4칸을 주었는데 아래 문장이 공백 5칸을 주면 다른 구문으로 판단하고 에러를 발생시킨다.

<br>

### *If-else*
``` py
if Conditional_Expression:
    Statement1  # 조건식(Conditional_Expression)이 True이면 동작
else:
    Statement2  # 조건식(Conditional_Expression)이 False면 동작

#e.g.
if (1+1)==3:  # It's False
    print("It's True") 
else:
    print("It's False")
```

조건에 따라서 실행되야 하는 문장이 다른경우, If-else문을 사용한다.

> If와 else는 같은 레벨의 문장으로 들여쓰기 레벨(공백의 수)는 같아야 한다.

<br>

### *If-elif-else*
``` py
if Conditional_Expression1:
    Statement1  # 조건식1(Conditional_Expression1)이 True이면 동작
elif Conditional_Expression2:
    Statement2  # 조건식2(Conditional_Expression2))이 True이면 동작
else:
    Statement3  # 조건식(Conditional_Expression)이 False면 동작

#e.g.
if (1+1)==3:  # It's True2
    print("It's True1") 
elif (1+1)==2:
    print("It's True2") 
else:
    print("It's False")
```

조건에 따라서 실행되야 하는 문장이 다르며, 개수가 여러개인 경우, If-elif-else문을 사용한다.

- else는 생략이 가능하지만, 예상치 못한 동작이 발생할 수 있다는 점을 유의해야 한다.

    
주의 사항
- if는 분기를 나누는 제어문이지만, 기본적으로 모든 문장을 순차문이기에 위에서부터 읽어 내려옴

- 분기라는 말 답게, 하나를 선택하여 실행했으면 다른 문장을 선택/실행 할 수 없다.
    - 조건이 여러 if에 해당될 때가 있는데, 하나의 if에 해당되어 내부 문장을 실행 시켰으면 그 외의 if, elif, else문은 무시하고 넘어가게 된다.

<br>

### *If : ternary operators*
If-else문의 변형, 기본적으로 4줄이 나오는 if-else문을 1줄로 작성할 수 있는 방식이다.

- 조건문으로 실행되는 문장이 1줄이어야 작성이 가능함

> 가시성이 좋은지 나쁜지에 대해서는 의견이 분분하다. 개인적으로는 짧은 문장을 작성할 때는 간결하고 가시성이 더 나은 듯

``` py
True_Statement if Conditional_Expression else False_Statement

#e.g.
print("It's True") if (1+1)==3 else print("It's False")  # It's False
```

if 앞에 참일때 동작할 문장을 작성하고, if+조건식+else 후 거짓일 때 동작할 문장 작성 하는 방식이다.

- elif는 사용할 수 없지만, 중첩을 통하여 비슷한 동작을 할 수 있다.

```py
# 중첩된 삼항 연산 if문
# TS : 참일때 문장, CE : 조건식, FS : 거짓일 때 문장
TS1 if CE1 else TS2 if CE2 else FS

# e.g.
print("It's True1") if (1+1)==3 else \
print("It's True2") if (1+1)==2 else print("It's False")  # It's True2
```
- 최초 if 조건식이 거짓이면 두번째 if로 넘어가고, 여기서 참/거짓을 판별하여 참이면 두번째 참문장을 실행하는 방식

> 우유가 500원 이하면 2개, 1000원 이하면 1개, 그 이상은 구매하지 않는다고 하면 다음과 같이 작성이 가능하다.
``` py
buy_func(2) if milk_price<=500 else \
buy_func(1) if milk_price<=1000 else buy_func(0)
```