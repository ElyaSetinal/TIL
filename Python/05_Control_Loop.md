## **제어문02, Control Statement02 : 반복문**

> 제어문이란 : 프로그램 흐름을 제어하는 경우에 사용 되는 실행문

## **반복문, loop**
반복문 : 조건을 만족하는 동안 특정 문장을 반복 동작 시키는 문장
- for, while

### *for*
``` py
for Variable in Iterable_Data:
    Statement

#e.g.
for i in range(5):
    print(i, end=',')  # 0, 1, 2, 3, 4
```
- range()함수는 주로 반복문에서 자주 사용하는 내장함수중 하나로, 일정한 값의 범위를 list 형태로 반환한다.
    > range ( start|default=0, end, step|default=1 ) <br> start값과 step값은 생략이 가능하다.
- 다른 언어에서도 비슷하지만, for문은 `반복 횟수`에 초점이 맞추어진 반복문이다.
- in 뒤에는 반드시 Iterable, 순차적(순서 유무 무관)으로 값을 하나씩 반환할 수 있는 자료가 와야한다.
- Iterable한 값이 변수에 하나씩 들어가면서, 반복 횟수를 만들고 동시에 변수로써 사용된다.
    ``` py
    # 반복 횟수이자 변수인 이유
    for i in "Hello":
        if i=="l":
            print("1")
        else:
            print("0")

    ''' result
    0
    0
    1
    1
    0
    '''

    # Iterable인 String인 "Hello"가 for문의 데이터로 들어왔고, for문은 이 "Hello"를 하나씩 i 에 입력하여 if문을 구동시키는 예시 문장이다.
    ```

<br>

#### *List Comprehension*
> 기존 리스트를 가공하여 새로운 리스트를 생성 및 반환하는 기술

리스트를 작성하거나 변환해야 할 때, 간결하게 작성할 수 있다는데 장점이 있다.

``` py
# 기본 방식
Variable = [ Statement for Loop_Variable in Iterable_Data ]

# 예시
result = []
for i in [1, 2, 3, 4]:
    result.append(i*2)
print(result)  # [2, 4, 6, 8]

# List Comprehension 적용
result = [(i*2) for i in [1, 2, 3, 4]]
print(result)  # [2, 4, 6, 8]
```

- for문 내부에 들어갈 문장을 for문 앞에 작성하고, for문을 작성하면 된다.

- Iterable_data에는 dict를 제외한 모든 Iterable 자료형이 들어갈 수 있고, 결과는 list형이 된다.
    - Iterable_Data가 문자열인 경우에는 주의를 요하는데, 특정 연산이나 함수는 문자열에 적용 할 수 없어서 에러가 발생하기 쉽다.

- if문을 추가하면 조건부로 동작 할 수 있다.
``` py
# 조건부 반환(if)
Variable = [ Statement for Loop_Variable in Iterable_Data if Conditional_Exp. ]  # 마지막에 if + 조건식 추가

result = [(i*2) for i in [1, 2, 3, 4] if i%2==0]
print(result)  # [4, 8]


# 3항 연산자 조건부 반환
Variable = [ True_State if Conditional_Exp. else False_State for Loop_Variable in Iterable_Data ]  # 3항 연산자 방식인 True if 조건식 else false 를 for 앞에 추가

result = [(i*2) if i%2==0 else 0 for i in [1, 2, 3, 4] ]
print(result)  # [0, 4, 0, 8]
```

<br>

#### *Dict Comprehension*
> List Comprehension과 유사하게, dict를 가공하여 새로운 dict를 생성 및 반환하는 기술

작성 방법이나 구조는 List Comprehension과 동일하지만, key:value 쌍으로 움직인다는 점이 차이가 난다.

``` py
Variable = { Statement for Key_Vari.,Value_Vari. in Dict_Data.items() }
# .items로 인하여 key와 value가 하나의 튜플로써 반환되므로, 이 모두를 받기 위해 loop 변수가 두개여야 한다.

# 예시
d = {"a":10, "b":20}
d_comp = {v:k for k,v in d.items()}
print(d_comp)  # {10: 'a', 20: 'b'}

# 조건부 반환
Variable = { Statement for Key_Vari.,Value_Vari. in Dict_Data.items() if Conditional_Exp. }

# 3항 연산자 조건부 반환
Variable = { True_State if Conditional_Exp. else False_State for Key_Vari.,Value_Vari. in Dict_Data.items() }
```

<br>

#### *Generator Expression(Comprehension?)*
> 제네레이터 객체를 생성하는데 사용되는 수식<br>[정리가 잘 된 글, tistory plas님](https://plas.tistory.com/50)

제네레이터(Generator)는 연속된 값을 차례대로 반환하는 함수와 유사한데, 요청이 있을 때 마다 하나씩 생성하여 반환한다.

``` py
Variable = (Statement for Loop_Variable in Iterable_Data)
# Tuple Comprehension이 아니다!
```

- 소괄호를 사용하여 제네레이터 수식을 작성한다.

- 큰 데이터를 처리하는데 주로 사용되며, 무한한 계산도 가능하다는 장점이 있다.

- for 구문의 Iterable_Data나 next() 함수로만 접근이 가능하다. 
    ``` py
    for i in generator:
        print(i)

    print(next(generator))
    ```

한계점
- 한번 사용하고 나면 더이상 사용할 수 없는, 휘발성을 가진다.
- 인덱스를 통하여 접근 할 수 없고, 길이등 상태를 확인하는 함수도 사용할 수 없다.
- 실제 데이터를 갖는 것이 아닌, Generator라는 말대로 데이터 생성기를 하나 만든 것과 같다고 생각하자.

<br>

### *While*
``` py
while Conditional_Expression:  # while+조건식
    Statement  # 실행 될 문장 
```

for가 횟수에 포커싱을 했다면, while은 조건에 포커싱이 된 반복문이다.
- 정확한 횟수를 알 수 없거나, 특정 조건을 만족했을 때만 동작하기를 바라는 경우 while

조건식이 True 일때만 동작하는데 자칫 잘못하면 무한 반복을 하는 문제가 있다.
- 보통 while 반복문 내부에 조건식에 영향을 줄 수 있는 식이 같이 들어가서 False로 만드는 경우가 많다.

### *Break, Continue*
반복문과 자주 같이 쓰이는 구문으로, 각각의 동작은 아래와 같다.
- break : 반복 문장을 탈출한다.
- continue : 이후 문장을 건너뛴다.

``` py
# Break 동작
while 1:  # 무한 반복
    print(1)
    print(2)    
    break
    print(3)  # 동작하지 않음
print(4)

# 결과
'''
1
2
4
'''

# Continue 동작
for i in [1,2,3,4]:
    if i == 2:  # i가 2이면 for문으로 돌아감
        continue
    print(i)

# 결과
'''
1
3
4
'''
```

for든 while이든 반복문을 하나의 블록으로 놓고 생각하면..
- break는 블럭 내부에서 이후 문장을 무시하고 블록을 깨고 나가는 것이고, continue는 블럭 내부에서 이후 문장을 무시하고 새로 시작하는 것이다.
- Break 동작 예시에서도 보이지만, 반복문 밖의 문장은 해당되는 대상이 아니다.