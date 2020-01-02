# 반복문

## while

```c
int i = 0;
while (i<10) //i가 10보다 작을 경우, 계속해서 수행.
{
   printf("i is less than 10! [%d]\n",i);
   i++; //반복될 때마다 1씩 증가.
}
```

> 무한 루프로 들어간 경우, `ctrl+c`를 누름. 키보드 인터럽트로 나오게 됨.

위의 루프에서 반복되는 block은 다음과 같이 한 줄로 바꿀 수 있으며, 한 줄인 경우 curl bracket을 생략해도 됨.

```c
int i = 0;
while (i<10)
   printf("i is less than 10! [%d]\n",i++);
```

* `while`문은 뒤에 오는 조건문이 true인 경우 반복 block을 실행함.
* 조건문이 false인 경우엔, 반복 block을 실행하지 않고 나오게 됨.

```c
while (1){
   printf("This is infinite loop!\n");
}
```

### 구구단 출력하기.

```c
#include <stdio.h>

int main(void){

   int i = 2;
   int j = 1;
   
   while (i<=9)
   {
      j = 1;
      while (j<=9)
      {
         printf("%2d * %2d = %2d \n", i, j, i*j);
         j++;
      }
      i++;
   }

   return 0;
}
```

## `do` `while` 문

* while의 변종?
* 한번은 무조건 실행되고 이후 반복여부를 체크 (`while`의 경우 실행하기전에 체크를 했음을 기억)

```c
int i =0;
do
{
   printf("Hello, world!\n");
   i ++;
}while(i<10);
```

## `for`문

* 가장 많이 이용되는 반복문.
* 초기값(expression), 반복조건(expression), 증감정도(expression) 를 지정하여 반복을 수행.

```c
for (int i=2;i<10;i++)
{
   for (int j=1;j<10;j++)
   {
      printf("%2d * %2d = %2d \n", i, j, i*j);
   }
}
```

> 구형 c compiler에서는 초기값을 지정할 때, 변수 선언을 못하는 경우도 있음.
> 이 경우, for문 외부에서 선언하고 값만 할당하는 형태로 사용하면 됨.


다음의 실행결과는?

```c
for (;;){
   printf("test!!!\n");
}
```

증감이라고 한 이유는 다음과 같이 감소도 가능함.

```c
for (int i=10;i>0;i--)
{
   printf("%2d\n", i);
}
```


   
