# Chapter11. 1차원 배열
# 11-1. 배열의 이해와 배열의 선언 및 초기화 방법
## 1. 배열(Array)이란
다수의 데이터를 저장하고 처리할 수 있는 데이터 타입. 즉, 둘 이상의 변수를 모아 놓은 것.

예를 들어, 1~100 사이의 정수 변수를 선언한다고 했을 때, 변수를 100개를 선언하지 않고 하나의 변수에 선언 가능
![](2019-12-27-05-05-17.png)

* 특징
1. 한 번에 둘 이상의 변수 선언 가능
2. 하나의 배열에 여러가지 자료형 불가
3. 값들이 나란히 선언됨.
 
### **<array_name_type.c>**
```c
#include <stdio.h>

int main(void) {
	int arr[3] = { 0,1,2 };
	printf("array_name: %p \n", arr);  //%p는 주소값 출력에 사용되는 서식문자
	printf("first index: %p \n", &arr[0]); //&연산자는 변수의 주소 값을 반환
	printf("second index: %p \n", &arr[1]);
	printf("third index: %p \n", &arr[2]);

	return 0;
}
```
```
array_name: 0000006AD4AFF7C8 // 배열 이름과 첫 번째 인덱스의 주소값이 같다.
first index: 0000006AD4AFF7C8  // 인덱스 값이 1씩(int 형) 차이나기 때문에 주소값이 4씩 차이난다.
second index: 0000006AD4AFF7CC
third index: 0000006AD4AFF7D0
```    




## 2. 배열 선언하기
>### 필요한 것
>* 배열명
>* 자료형
>* 배열 길이 정보

<예시>
>```int oneDimArr[4]```
>* int 배열을 이루는 요소(변수)의 자료형
>* oneDimArr 배열명
>* [4] 배열의 길이


## 3. 배열에 접근하기
```c
int arr[3]; // 길이가 3인 int형 1차원 배열 선언
arr[0]=10; // 배열 arr의 첫 번째 인덱스에 10을 저장
arr[1]=20; // 배열 arr의 두 번째 인덱스에 20을 저장
arr[2]=30; // 배열 arr의 세 번째 인덱스에 30을 저장
```
> **arr[inx]=20;** // 배열 arr의 idx+1번째 인덱스에 20을 저장하라는 뜻

### **<array_access.c>**
```c
#include <stdio.h>

int main(void)
{
	int arr[5];
	int sum = 0, i;
	
	arr[0] = 10, arr[1] = 20, arr[2] = 30, arr[3] = 40, arr[4] = 50; // 배열 arr의 첫 번째부터 다섯 번째 인덱스까지 차례로 10, 20, 30, 40, 50을 저장

	for (i = 0; i < 5; i++) {
		sum += arr[i];
	} // 배열 arr의 인덱스 값을 첫 번째부터 차례로 sum에 더한다

	printf("배열요소에 지정된 값의 합: %d \n", sum);
	return 0;
}
```
### Warning
```c
int arr[3];
arr[0]=1, arr[1]=2, arr[2]=3, arr[3]=4; 
```
> 디버그는 되지만 경고문이 뜬다.

## 4. 배열 초기화
1. 
    ```int arr1[5]={1,2,3,4,5}```  

2.  
    ```int arr2[]={1,2,3,4,5,6,7} ```  
    배열의 길이를 생략하더라도 컴파일러에 의해 자동으로 길이정보를 채워줌.

3.
    ```int arr3[5]={1,2};```  
    첫 번쨰 인덱스부터 순차적으로 값을 채워나가되, 채울 값이 존재하지 않는 나머지 인덱스들은 0으로 채워진다. 

### **<array_init.c>**
```c
#include <stdio.h>

int main(void) {
	int arr1[5] = { 1,2,3,4,5 };
	int arr2[] = { 1,2,3,4,5,6,7 };
	int arr3[5] = { 1,2 };
	int arr1_len, arr2_len, arr3_len, i;

	printf("배열의 arr1의 크기: %d \n", sizeof(arr1));
	printf("배열의 arr2의 크기: %d \n", sizeof(arr2));
	printf("배열의 arr3의 크기: %d \n", sizeof(arr3));
    
    // 배열의 크기를 그 배열의 자료형의 크기로 나누면 배열의 길이를 구할 수 있다. 
	arr1_len = sizeof(arr1) / sizeof(int); 
	arr2_len = sizeof(arr2) / sizeof(int);
	arr3_len = sizeof(arr3) / sizeof(int);
	// 배열의 인덱스 값 출력하기
	for (i = 0; i < arr1_len; i++)
	{
		printf("%d ", arr1[i]);
	}
	printf("\n");
	
	for (i = 0; i < arr2_len; i++)
	{
		printf("%d ", arr2[i]);
	}
	printf("\n");

	for (i = 0; i < arr3_len; i++)
	{
		printf("%d ", arr3[i]);
	}
	printf("\n");
	return 0;
}
```
```
배열의 arr1의 크기: 20
배열의 arr2의 크기: 28
배열의 arr3의 크기: 20
1 2 3 4 5
1 2 3 4 5 6 7
1 2 0 0 0
```
# 11-1. Question
## Q. 11-1-1 
### 길이가 5인 int형 배열을 선언해서 프로그램 사용자로부터 총 5개의 정수를 입력 받자. 그리고 입력이 끝나면 다음의 내용을 출력하도록 작성해보자.
* 입력된 정수 중에서 최댓값
* 입력된 정수 중에서 최솟값
* 입력된 정수의 총 합  
```c
#include <stdio.h>

int main(void) {
	int arr[5] = {};
	int min=0, max=0, i=0;

	for (i = 0; i < 5; i++) {
		printf("정수를 입력하시오: ");
		scanf_s("%d", &arr[i]);
		printf("%d \n", arr[i]);
		if (arr[i] < min) {
			min =arr[i];
		}
		if (arr[i] > max) {
			max = arr[i];
		}
	}
	printf("최댓값: %d \n", max);
	printf("최솟값: %d \n", min);
	return 0;
	
}
```
```
정수를 입력하시오: 5
5
정수를 입력하시오: 0
0
정수를 입력하시오: -2
-2
정수를 입력하시오: 4
4
정수를 입력하시오: 9
9
최댓값: 9
최솟값: -2
```
## Q. 11-1-2
### char형 1차원 배열을 선언과 동시에 다음 문장의 내용으로 초기화하고, 초기화 이후에는 저장된 내용을 출력해보자.
```c
#include <stdio.h>

int main(void) {
	char str[] = "Good time";
	printf("%s", str);
	return 0;
}
```
```
Good time
```

# 11-2. 배열을 이용한 문자열 변수의 표현
## 1. char형 배열의 문자열 저장과 '널(null)' 문자
```char str[14]="Good morning!";```  
* 위와 같은 코드로 배열에 문자열 저장 가능  
* 배열의 길이 정보 생략 가능
* 문자형이 저장된 char형 배열의 길이는 문자열의 끝에 '\0'(null문자)이라는 escape sequence가 자동으로 삽입돼 실제 *문자열의 길이+1*이다.
    * 널문자를 이용해 문자열의 끝을 표시 (메모리상에서 문자열은 이진 데이터로 저장되기 때문에 문자열의 시작과 끝을 표시해 주지 않으면 문자열 구분 X)

### **<array_string.c>**
```c
#include <stdio.h>

int main(void) {
	char str[] = "Good morning!";
	printf("배열 str의 크기: %d \n", sizeof(str));
	printf("널 문자 문자형 출력: %c \n", str[13]);
	printf("널 문자의 정수형 출력: %d \n", str[13]);

	str[12] = '?';
	printf("문자열 출력: %s \n", str);
	return 0;
}
```
```
배열 str의 크기: 14 // 문자열의 길이는 13이지만, 마지막 널 문자를 포함하면 14
널 문자 문자형 출력:
널 문자의 정수형 출력: 0
문자열 출력: Good morning?
```
> 널 문자의 아스키 코드 값은 0이므로 정수형은 0으로 출력하며 문자형태로는 아무것도 출력하지 않는다.

### **<start_end_string.c>**
```c
#include <stdio.h>

int main(void) {
	char str[50] = "I like C programming";
	printf("string: %s \n", str);

	str[8] = '\0'; 
    // 널문자의 아스키 코드 값이 0이므로 '\0'을 0으로 작성해도됨.
	printf("string: %s \n", str);

	str[6] = '\0';
	printf("string: %s \n", str);
	
	str[1] = '\0';
	printf("string: %s \n", str);
	return 0;
}
```
```
string: I like C programming
string: I like C
string: I like
string: I
```
> 널 문자에 의해 변경된 문자열의 끝을 기준으로 문자열이 출력됨.

## 2. scanf 함수를 이용한 문자열의 입력
### **<read_string.c>**
```c
#include <stdio.h>

int main(void) {
	char str[50];
	int idx = 0;

	printf("문자열 입력: ");
	scanf_s("%s", str, sizeof(str)); // sizeof 연산자가 있어야 실행됨
	printf("입력 받은 문자열: %s \n", str);
	printf("문자 단위 출력: ");
	while (str[idx] != '\0')
	{
		printf("%c", str[idx]);
		idx++;
	}
	printf("\n");
	return 0;
}
```
> * 문자열을 입력 받는 배열의 이름 앞에는 &연산자를 붙이면 안됨.
> * scanf 함수호출을 통해 입력 받은 문자열의 끝에도 널 문자가 삽입
> * 널 문자가 존재하면 문자열이고 널 문자가 존재하지 않으면 문자열이 아님.
> * scanf 함수가 데이터를 구분 짓는 기준은 공백이다.
* 문자열 중간에 공백이 있는 경우
```
문자열 입력: Kim nayeon
입력 받은 문자열: Kim
문자 단위 출력: Kim
```
* 문자열 중간에 공백이 없는 경우
```
문자열 입력: Kimnayeon
입력 받은 문자열: Kimnayeon
문자 단위 출력: Kimnayeon
```

## Q. 11-2-1
### 프로그램 사용자로부터 하나의 영단어를 입력 받아서 입력 받은 영단어의 길이를 계산해 출력하는 프로그램을 작성해보자. 
```c
#include <stdio.h>

int main(void) {
	char word[100];
	int word_len = 0;

	printf("영단어를 입력: ");
	scanf_s("%s", word, sizeof(word));

	while(word[word_len] != '\0') { // 널 문자를 만나기 전까지 단어 길이 세기(널 문자를 만나면 while문 종료)
		word_len++;
	}
	printf("영단어의 길이: %d \n", word_len);
	return 0;
}
```
```
영단어를 입력: programming
영단어의 길이: 11
```
## Q. 11-2-2
### 프로그램 사용자로부터 영단어를 입력 받아서 char형 배열에 저장한다. 그 다음 배열에 저장된 영단으를 역순으로 뒤집는다. 물론 이 때에 널 문자의 위치를 변경해서는 안 된다. 뒤집고 나서는 제대로 뒤집혀졌는지 확인하기 위해 출력해보자.
```c
#include <stdio.h>

int main(void) {
	char word[100];
	int word_len = 0, i; 
	char temp;

	printf("영단어를 입력: ");
	scanf_s("%s", word, sizeof(word));

	while (word[word_len] != '\0') {
		word_len++;
	}

	for (i = 0; i < word_len / 2; i++) {
		temp = word[i];
		word[i] = word[(word_len - i) - 1];
		word[(word_len - i) - 1]=temp;
	}
	printf("뒤집힌 영단어: %s \n", word);
	return 0;
}
```
```
영단어를 입력: kimnayeon
뒤집힌 영단어: noeyanmik
```

## Q. 11-2-3
### 프로그램 사용자로부터 영단어를 입력 받고, 구성하는 문자 중 아스키 코드의 값이 가장 큰 문자를 찾아서 출력하는 프로그램을 작성해보자.
```c
#include <stdio.h>

int main(void) {
	char word[100];
	int word_len = 0, i; 
	char max = 0;

	printf("영단어를 입력: ");
	scanf_s("%s", word, sizeof(word));
// 영단어 길이 계산(널 문자 제외)
	while (word[word_len] != '\0') {
		word_len++;
	}
	
// max값 구하기
	for (i = 0; i < word_len ; i++) {
		if (max < word[i]) {
			max = word[i];
		}
	}
	printf("아스키 코드 값이 가장 큰 문자: %c \n", max);
	return 0;
}
```
```
영단어를 입력: cprogramming
아스키 코드 값이 가장 큰 문자: r
```
