## **Statement, 문장**

> 거의 모든 프로그래밍 언어가 그렇겠지만, 특별한 키워드가 있지 않는 한 순차문으로, 차례대로 진행된다.

- python은 들여쓰기가 하나의 의미를 갖지만, JS를 포함한 그 외의 언어들은 들여쓰기는 순수한 가독성 이슈로 사용한다.

<br>

### *제어문(Control Statement) - 단일 if문*
``` JS
if(조건식) {
    Statement
};
```
- 소괄호 내부의 조건식이 True면 if 문장이 실행, False면 실행되지 않음
- { } 블록 표기는 옵션사항이지만, 가독성과 문장 구분을 위하여 쓰는 것이 좋다. 만일 if문 내부가 여러줄이라면 반드시 써야한다.

#### *prompt, DataTrans_int*
``` JS
Variable_name = prompt("Message");

/* 수치형 변환 */
Number.parseInt(Variable_name);
// 또는
parseInt(Variable_name);

```
python의 input() 함수, C언어의 scanf() 함수처럼 키보드로 입력받기 위해서 사용하는 prompt()

prompt로 입력을 받으면 문자열이 되기 때문에, 연산을 위해서 수치형으로 바꾸어 주는 parseInt()

parseInt()와 Number.parseInt()는 위치가 조금 다르다.    
- parseInt() : Window 객체에 존재    
- Number.parseInt() : Number 객체에 존재, 권장사항   

<br>

### *제어문(Control Statement) - if-else문*
``` JS
if(조건문) {
    Statement;
}
else {
    Statement;
};
```
- 조건문이 true면 if가, false면 else의 문장이 실행된다.

<br>

### *제어문(Control Statement) - 다중 if문*
``` JS
if(조건문) {
    Statement;
}
else if(조건문) {
    Statement;
}
else {
    Statement;
};
```
- 다중 조건일때 사용하며, 순차적으로 조건문을 확인한다.

<br>

### *제어문(Control Statement) - Switch-Case 문*
``` JS
switch(Variable_name) {
    case Value1: Statement1; break;
    case Value2: Statement2; break;
    case Value3: Statement3; break;
    default: Statement;
};
```
변수명이 값과 일치하는지 확인하여, True면 그 뒤의 문장(Statement)가 실행된다.
- case의 문장만큼 if문/else if문+동등비교 를 쓰는 것과 동일하다. 
- 동등을 제외한 비교 연산은 불가능한 만큼, 상황에 맞추어서 사용한다.

break는 필수가 아닌 옵션이지만, 사용하지 않으면 최초 동등비교가 성립한 문장부터 이후 문장이 모두 실행된다.
- 위의 예시에서 변수가 Value2라는 값을 가지면, 문장2, 3 모두 실행된다는 이야기

<br>

### *반복문(Iteration Statement, loop) - for문*
원하는 횟수만큼 반복하기 위해서 [시작값, 증감, 조건식], 3가지가 필요로 한다.

``` JS
for(Initial_Value; 조건식; 증감식) {
    Statement;
};

/*
for(i=0; i<10; ++i) {
    Statement;
};
*/

```
순서는 다음과 같다.
1. 변수가 초기값을 가지고 조건식에 입력 
2. 조건식이 True를 반환하면 Statement를 동작 
3. 동작이 완료되면 증감식으로 이동하여 변수 증감 
4. 조건식이 False가 될 때까지 반복 
5. False가 나오면 for문 종료

- 반복 횟수 예측이 쉽기때문에, 횟수가 정해져있는 반복문에 사용하는게 좋다.

- Allocation 변수 선언 처럼 for문에도 변수를 동시에 선언할 수 있다.
    ``` JS
    for(i1=0, i2=10; i1<10 && i2>0; ++i1, i2+=2) {
        statement;
    };
    ```

- for 문장 내에 break와 continue를 사용할 수 있다.
    - break는 for문을 강제 종료한다. (블록의 바깥으로 포인터가 이동)
    - continue는 continue 이하의 문장을 무시한다 (블록의 끝으로 포인터가 이동)

<br>

### *반복문(Iteration Statement, loop) - while문*

python의 while문과 문법 구조적으로 큰 차이는 없다.

``` JS
let Variable_name = Initial_Value; // 초기식, 변수에 초기값 할당
while (조건식) {  // 조건식이 true인 동안에 동작
    Statement;
    Variable_name 증감식; // ++Variable_name이나, Variable_name-- 같이 증감 연산자 사용해도 되고, 아니면 식으로써 입력해도 된다.
};
```

- 반복 횟수 예측이 어렵기 때문에, 반복횟수가 필요하기보다는 조건이 중요할 때 사용하는게 좋다.
    - 비교 조건이 만족이 중요하다 : while, 반복 횟수가 중요하다 : for

- for와 마찬가지로, break와 continue 키워드 사용이 가능하다.

<br>

### *반복문(Iteration Statement, loop) - do-while문* 

while이 조건에따라 한번도 실행되지 않을 수 있는데 비해, do-while은 적어도 한번은 실행되는 차이가 있다.
- 잘 안쓰이는 문장

``` JS
let Variable_name = Initial_Value; 
do { 
    Statement;
    Variable_name 증감식;
} while (조건식);
```