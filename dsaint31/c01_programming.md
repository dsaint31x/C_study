# basic 01 

## idnetifier (식별자)

* 변수명 및 함수명 등으로 사용됨.
* 영문 대문자, 소문자, 숫자, 밑줄로 구성됨.
* 단 숫자의 경우 맨 앞에 올 수 없음.
* case sensitivity.

## reserved word (예약어)

* compiler에게 특정 의미가 부여된 단어.
* keyword라고도 불림.
* identifier로 사용 불가.

| type | |
|---|---|
|자료형| void, char, short, int, long, float, double, unsigned, struct, union, enum, const |
|storage class | auto, static, extern, register |
|control statment | if, else, switch, case, break, continue, return, goto |
|iteration | for, while, do|
|etc. | sizeof, typedef |

## commnet (주석)

* compiler가 읽지 않으며 프로그래머의 보다 쉽게 프로그램 소스를 파악하도록 도와줌.
* 일종의 소스 내의 메모에 해당.
* `//` slash를 두개로 한 줄을 주석 처리.
* `/* ~~~ */` 는 여러 라인을 묶어서 주석 처리.

## C 언어의 기본 단위 : Function
* C언어는 절차지향적 언어
   * function을 만들고(정의), 해당 function들의 실행(호출, call)순서 및 실행 조건을 결정하는 것이 주요 task.
* function은 head와 body로 구성됨.
* function에서의 입력은 parameter로 정의되고, arugment들이 parameter에 할당되어 입력이 이루어짐(function의 call단계에서 이루어짐).
  
## main 함수
* 프로그램의 시작점.
* 오직 한 프로그램에 하나의 main함수만이 허용됨.
```c
int main (int argc, char* argv[])
{
}
```

```c
# include <stdio.h> // stdio library를 include. (preprocessing)

int main (void) // head
{ //start of body
   printf("Hello world! \n"); //call of printf function.
   return 0; //normal finish. 
} //end of body
```
* `printf`는 standard function(표준함수)로서 standard library(stdio)에 속해 있음.
* 프로그래머들을 위해 수많은 function들이 이미 표준으로서 정의되어 있고 제공됨.
   * 바퀴를 다시 만들지 말 것.

## statment
* C에서 statemnt는 일반적으로 `;`semicolon으로 끝남.
* 가급적 한 line에 한 statment로 구성하는게 가독성이 좋음.

## conversion specifier (서식문자)

* `printf`에서 변수들을 출력할 때, 출력의 형태를 지정하는 용도로 사용되는 문자.
* `%x`의 형태를 가짐.
* `escape sequence`와 함께 기억을 해두어야 하는 부분.

## library (라이브러리)

* S/W를 개발할 때 재사용가능한 비휘발성의 자원들의 모임을 가리킴.

