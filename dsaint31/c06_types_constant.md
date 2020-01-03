# 자료형과 상수

시작하기 전 variable(변수)의 개념을 다시 확인할 것.

> **variable**이란 숫자, 문자 등의 데이터들이 저장되는 메모리 공간을 의미함.
>
> 메모리에 저장된 데이터는 *메모리 주소*와 차지하고 있는 *메모리 크기*를 가지지만, 프로그래밍 언어에서는 **variable**를 이용하여 해당 varaiable의 **이름**을 통해 해당 값을 접근하게 됨.

## 자료형

* 데이터를 표현하는 기준.
* 변수 나 상수의 크기 및 표현범위를 결정함.

## 기본 자료형 (Data Types)

### 정수 integer

* MSB가 sign을 나타냄.
* `unsigned`가 붙을 경우, 양수만을 표현하게 됨. (정수형 type에만 unsigned 가 붙을 수 있음)
* `signed`를 붙일 수도 있으나 `char`를 제외하곤 안 붙은 경우와 같음.

| type | bytes | (gcc 7.4.0 64bit, Mint)|
|---|---|---|
|char| 1 bytes | -128~127|
|unsigned char | 1 bytes | 0~255 |
|short | 2 bytes | -32,768 ~ 32,767 |
|unsigned short | 2 bytes | 0 ~ 65,535 |
|int | 4 bytes | -2,147,483,648 ~ 2,147,483,647 |
|unsigned int | 4 bytes | 0 ~ 4,294,967,295 |
|long | 8 bytes | -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807|
|unsigned long | 8 bytes| 0 ~ 2^64-1|
|long long | 8 bytes | -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807|
|unsigned long long | 8 bytes | 0 ~ 2^64-1|

### 실수 float

* IEEE754 참조.
* `float`가 정밀도가 `double`에 비해 2배 가량 낮음.
* 연산속도 측면에서도 64bit OS라면, double을 권장함. (같거나 빠른 속도를 보임)
   * `float`는 일반적으로 의료 데이터의 저장포맷. 데이터 크기 면에서 장점을 보이므로 영상데이터들은 보통 float임.

| type | bytes | 
|---|---|---|
|float | 4 bytes |
|double | 8 bytes |
|long double | 16 bytes |
* (gcc 7.4.0 64bit, Mint)

```c
#include <stdio.h>

int main(void) 
{
   double r;
   double a;
   
   printf("Enter radius:\n");
   scanf("%lf",&r); // double을 입력받을 때는 lf
   a = r*r*3.14;
   printf("area:%f\n",a); // 출력의 경우, float나 double이나 f임.
   return 0;
}
```

### 문자 character

* c에서는 기본적으로 ascii코드로 문자가 표현됨. (흔히 표준을 지키는 경우 ANSI C라고 불리기 때문에 역시 ANSI에서 만든 ascii코드를 사용.)
   * American National Standard Institute (ANSI)
   * ASCII (American Standard Code for Infomration Interchange)
* `char`로 표현되며, 1byte임. (어떤 컴파일러에서는 `unsinged char`와 같으며 `signed char`와는 다른 경우가 존재함.)

```c
#include <stdio.h>

int main (void) 
{
   char a = 'A';
   char b = 65;
   printf ("%c / %c \n",a,b);
   printf ("%d / %d \n",a,b);
   return 0;
}
```

## 상수 (constant, literal)

### literal 상수

* variable과 달리, **이름이 없는 상수**를 가르킴.
* `literal constant`가 원래 이름이나, 대부분 `literal`이라고 애기함

> **literal**
> 
> "문자 그대로 직역" 이라는 뜻.
> literal－related to the exact meaning of words, without any room for creativity or interpretation
> * When Meghan said she was flooded with work, she didn't mean it literally.

* literal의 자료형도 `c`에선 컴파일 전에 정해짐 (어떻게 기재하느냐가 중요.)
```c
#include <stdio.h>

int main(void)
{
   int i = 5;
   float f = 5.f;
   double d = 5.;
   char a = 'A';
   char b = 65;
   printf("size of i:%lu bytes\n",sizeof(i));
   printf("size of literal 5:%lu bytes\n",sizeof(5));
   printf("size of f:%lu bytes\n",sizeof(f));
   printf("size of literal 5.f:%lu bytes\n",sizeof(5.f));
   printf("size of d:%lu bytes\n",sizeof(d));
   printf("size of literal 5.:%lu bytes\n",sizeof(5.));
   printf("size of a:%lu bytes\n",sizeof(a));
   printf("size of literal 'a':%lu bytes\n",sizeof('A'));
   printf("size of literal '65:%lu bytes\n",sizeof(65));

   printf("a and b: %c, %c\n",a,b);
   return 0;
}
```

* 자료형을 정해주는 접미사.
   |접미사 | 자료형 |  |
   |---|---|---|
   |u | unsigned int | unsigned int ui = 1024u; |
   |l | long | long l = 1000l; |
   |ul | unsigned long | unsigned long ul = 1000ul;|
   |ll | long long | long long ll = 1000ll; |
   |ull | unsigned long long | unsigned long long ull = 1000ull; |
   |f | float | float f = 3.f; |
   |l | long double | long double ld = 3.l; |
   
### symbolic constant : `const` 상수
 
* variable 처럼 이름을 가지지만, 상수 인 경우.
* `#define` macro를 이용하거나 `const` 키워드를 이용함.

> 관례적으로 대문자로만 구성된 이름을 가지며, 스페이스 대신 underbar가 이용됨.
>
> `MAX_NUM` 의 형태.
 
```c
const int MAX_ITER = 100;
```
 
## 형변환 type casting

* 일반적으로 연산자로 연산 수행시 피연산자의 type에 의해 결과의 type이 결정됨 (피연산자가 모두 같은 type일 경우, 결과도 같은 type)
   * 단, `int`의 경우,대표적인 정수형 type으로, `char`나 `short`로 구성된 expression의 연산 결과도 `int`가 됨.
   * `float`로 구성된 경우는 `float`로 `double`이 아님.
```c
#include <stdio.h>

int main(void)
{
   int i=3, j=4;
   double r;
   r = i/j;
   printf("%d / %d = %f \n",i,j,r);
   return 0;
}
```
* 피연산자의 type이 다를 경우, 묵시적인 형변환이 수행됨.
* 서로 다른 `type`의 값이 연산될 때는 `type`이 하나로 통일됨 (명시적으로 지정하지 않은 경우, 자동으로 수행됨).

### 묵시적인 형변환


* 암묵적인(자동으로 수행되는) **형변환**은 *데이터의 손실을 최소화하는 방향으로 수행*된다.
   * `char` op `char` > `int` op `int`
   * `char` op `int` > `int` op `int`
   * `int` op `double` > `double` op `double`
   * `char` op `double` > `char` op `double`
* 기본적으로 정수는 `int`로, 실수는 `double`임. 
* 묵시적으로 형변환시 큰 표현범위의 `type`으로 변환됨.
* `assign`의 경우엔, 왼쪽의 `type` 에 맞추어 변환됨. (데이터 손실 발생할 수 있음.)
   * `int resutl = 3.5; //소수값이 버려지는 데이터손실 발생.` 
   
### 명시적인 형변환

* 강제적 형변환이라고도 불림.
* 어떤 `type`으로 변환할지를 명시적으로 지정.
   * `int a = (int)3.14195;`
* 명시적 형변환에 사용되는 curly bracket을 가르켜서 type casting operator라고 부름 (우선순위가 매우 높아 거의 먼저 수행됨).   
```c
double time = 0.375;
int min;

time = time * 60;
min = (int)time;
time = time – min;

printf(“분 : %d\n”, min);
printf(“초 : %d\n”, (int)(time *60));
```

