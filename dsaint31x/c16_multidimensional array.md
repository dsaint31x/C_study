# C_16 multidimensional array  
> 발표 : 박은영
##### 윤성우의 열혈c프로그래밍 p.338

### 다차원 배열의 이해와 활용
## 1차원과 2차원배열의 선언형태


**자료형 배열이름[세로길이][가로길이];**

* int arr1[3]; // 길이가3인 1차원 int배열
* int arr2[7][9]; // 세로길이가 7이고 가로길이가 9인 2차원 int배열
* int arr3[7][8][9]; // 세로길이가 7이고 가로길이가 8이며 높이가 9인 3차원 int배열

### 다차원 배열은 sizeof연산자로 계산하기
크기는 바이트 단위로 계산된다.
 
```c
#include <stdio.h>

int main(void)
{
int arr1[7];
int arr2[8][9];
int arr3[8][9][10];
printf("길이가 7인 배열크기: %d \n", sizeof(arr1));
printf("세로길이가 8 가로길이가 9 인 배열크기 : %d \n", sizeof(arr2));
printf("세로길이가 8 가로길이가 9 높이가 10인 배열크기 : %d \n",sizeof(arr3));
return 0;
}
```
![3개](https://postfiles.pstatic.net/MjAyMDAxMTdfNzYg/MDAxNTc5MTkxNzY3MzUw.FU0Z-QgMyGb-aDZJPmHZgAEiad6TUYLc7kSsqtT5KRYg.3pefQOqRek_VJ9HQZL3JtiPQzuRx_u81v3xBycDjy7kg.PNG.luckeun0713/%EB%B0%B0%EC%97%B4%ED%81%AC%EA%B8%B0%EC%84%A0%EC%96%B8%EC%97%86%EC%9D%B4%EC%A0%80%EC%9E%A5.PNG?type=w580)

### 2차원 배열요소의 접근
int형 배열을 대상으로 세로n번째위치 가로m번째 위치에 저장된 값을 변경 및 참조하는 방법을 
일반화 할시 다음과 같다.  
arr[n-1][m-1];
printf("가로n 세로m번째 위치에 저장된 값 : %d /n,arr[n-1][m-1]);  

```c
#include<stdio.h>

int main(void)
{
	int arr[2][3];
	arr[1][2] = 20;

	printf("세로2 가로3에 저장된 값 출력 :%d \n" ,arr[1][2]);
		return 0;
}
```
>> ![text](https://postfiles.pstatic.net/MjAyMDAxMTdfMjM4/MDAxNTc5MTkxMzI5NTI2.3Mfmyys5zv21aG5BHabnsHloISLzEYCiSI1vDhkaZVgg.IIS_sTJ0697qb9FpzgHmQ0o7hGIKO8N6V73mgMDfZI4g.PNG.luckeun0713/3%EC%B0%A8%EC%9B%90%EB%B0%B0%EC%97%B4.PNG?type=w580)  
### 2차원 배열의 메모리상 할당의 형태
우리가 사용하고 있는 컴퓨터의 메모리는 2차원적 구조가 아니다.  
이는 메모리 주소값을 통해서 알 수 있다.  
메모리 주소값의 형태는 1차원적 구조이다.  

0x1001번지, 0x1002번지, 0x1003번지  

예를 들어서 0~5으로 초기화 된 세로길이3 가로길이2인 2차원 배열인 int arr[3][2] 메모리상의 구조는  

0x1000 **0** arr[0][0]  
0x1004 **1** arr[0][1]  
0x1008 **2** arr[1][0]  
0x100c **3** arr[1][1]   
0x1010 **4** arr[2][0]  
0x1014 **5** arr[2][1]  
  
으로 나타낼 수 있다.  

||1열[0]|2열[1]|
|------|---|---|
|1행[0]|0[0][0]|1[0][1]|
|2행[1]|2[1][0]|3[1][1]|
|3행[2]|4[2][0]|5[2][1]|

![표](https://postfiles.pstatic.net/MjAyMDAxMTdfNDkg/MDAxNTc5MTkxMzQyMjM3.L3d5P5CVBua6t3zmbsYZtRPD1mqN0fj4lrhrnY3BuKIg.A4Ev1bQ2rXfLmW7lf4KbnhgOLKfp5RtTqI-Ky3MAPj8g.PNG.luckeun0713/%EB%B0%B0%EC%97%B41.PNG?type=w580)


```c
#include <stdio.h>
int main (void)
{
int arr1[2][3];
int i,k;

for (i=0;i<2;i++)
for (k=0;k<3;k++)
printf("%p\n",&arr1[i][k]);
return 0;
}
```
![주소값](https://postfiles.pstatic.net/MjAyMDAxMTdfMTYw/MDAxNTc5MTkyMTU1MzI2.8JeQBgViqHeUrZALzNbIm90n0jcKM9kw88_yclg0hTQg.o4TXLEQ6XV1Di0SC2hoQBoylFXxORPwnZHg6rg1XdbQg.PNG.luckeun0713/%EC%A3%BC%EC%86%8C%EA%B0%92.PNG?type=w580)


## 실행화면  
0082FD5C  
0082FD60  
0082FD64  
0082FD68  
0082FD6C  
0082FD70    
C:\Users\박은영\source\repos\Project1\Debug\Project1.exe(7392 프로세스)이(가) 0 코드로 인해 종료되었습니다.  
이 창을 닫으려면 아무 키나 누르세요.
 
 ## 2차원 배열 선언과 동시에 초기화하기
 1차원 배열과 마찬가지로 2차원 배열도 선언과 동시에 초기화가 가능하다.  
**int arr[3][3] = {  
 {1,2,3},  
 {4,5,6},
 {7,8,9}  
 };** 
 
 초기화 리스트 안에는 행 단위로 초기화할 값들을 별도로 **중괄호({})** 로 명시해야한다.  
 일부 요소에 대해서는 초기화를 생략할 수 있다.  
 그리고 이렇게 해서 비게 되는 공간은 1차원 배열의 경우와 마찬가지로 0으로 초기화된다.  
 
 **int arr[3][3] = {  
 {1,},  
 {4,5},
 {7,8,9}  
 };** 
 
 이럴경우 빈 영역은 0으로 초기화 된다.  
 따라서 위 그림의 배열선언은 다음의 배열선언과 동일한다.  
 
 **int arr[3][3] = {  
 {1,0,0},  
 {4,5,0},
 {7,8,9}  
 };** 
  
   다음과 같이 하나의 중괄호 안에 초기화값을 순서대로 나열할 수도 있다.
   
   **int arr[3][3] = {  
   {1,2,3,4,5,6,7}  
   };**  
   
   부족한 영역은 0으로 초기화된다. 
   
   **int arr[3][3] = {  
   {1,2,3,4,5,6,7,0,0}  
   };**  
   
   ## 나타내보기 
   ```c
  #include <stdio.h>

int main(void)
{
	int i, k;

	/*2차원 배열 초기화의 예1 */
	int arr1[3][3] = {
		{1,2,3},
		{4,5,6},
		{7,8,9}
	};
	/*2차원 배열 초기화의 예2 */
	int arr2[3][3] = {
 {1,},
 {4,5},
 {7,8,9}
	};
	/*2차원 배열 초기화의 예3 */
	int arr3[3][3] = { 1,2,3,4,5,6,7,0,0 };

	for (i = 0;i < 3;i++)
	{
		for (k = 0;k < 3;k++)
			printf("%d", arr1[i][k]);
		printf("\n");
	}
	printf("\n");

	for (i = 0;i < 3;i++)
	{
		for (k = 0;k < 3;k++)
			printf("%d", arr2[i][k]);
		printf("\n");
	}
	printf("\n");

	for (i = 0;i < 3;i++)
	{
		for (k = 0;k < 3;k++)
			printf("%d", arr3[i][k]);
		printf("\n");
	}
	printf("\n");

	return 0;
}
```

![출력사진](https://postfiles.pstatic.net/MjAyMDAxMTdfOTYg/MDAxNTc5MTkxMzM0NTg2.mgC0AzL0axVrvMn_AQ1Yp97kl2ml2-otx6b3QoeKjgwg.TgMitnsq2HgUzdAQUp_RGSsqAjJVsr1RorrqK_OC0n8g.PNG.luckeun0713/%EC%BA%A1%EC%B2%98.PNG?type=w580)

## 배열의 크기를 알려주지 않고 초기화하기

1차원 배열선언시, 초기화 리스트가 존재한다면, 배열의 길이를 명시하지 않아도 됨을 기억할 것이다.  
2차원 배열선언시, 초기화 리스트가 존재한다면, 배열의 길이를 명시하지 않아도 된다.  
허나,2차원 배열선언의 경우 명시해야하는 배열의 크기가 가로세로 두개이다.  
**따라서 가로의 배열의 크기를 명시해줘야한다. 즉 세로 배열의 크기만 생략가능하다.**
```c
#include <stdio.h>

int main(void)
{
	int i, k;

	/* 2차원 배열 세로 크기없이 초기화 */
	int arr[][3]= {
		{1,2,3},
		{4,5,6},
		{7,8,9}
	};
	for(i = 0;i < 3;i++){
		for (k = 0;k < 3;k++)
			printf("%d", arr[i][k]);
		printf("\n");
	}

	return 0;
	}
```
![3차원1](https://postfiles.pstatic.net/MjAyMDAxMTdfNzYg/MDAxNTc5MTkxNzY3MzUw.FU0Z-QgMyGb-aDZJPmHZgAEiad6TUYLc7kSsqtT5KRYg.3pefQOqRek_VJ9HQZL3JtiPQzuRx_u81v3xBycDjy7kg.PNG.luckeun0713/%EB%B0%B0%EC%97%B4%ED%81%AC%EA%B8%B0%EC%84%A0%EC%96%B8%EC%97%86%EC%9D%B4%EC%A0%80%EC%9E%A5.PNG?type=w580)

 # 3차원 배열
 ### 3차원 배열의 논리적구조
 **자료형 배열이름[높이][세로길이][가로길이];**  
 
 * int  arr1[2][3][4]; // 높이2 가로3 세로4인 int형 3차원 배열
 * double arr2[5][5][5]; // 높이5 세로5 가로5인 double형 3차원 배열 
 
 ### sizeof연산자를 통해 3차원 배열 크기 확인하기
```c

 #include <stdio.h>

int main(void)
{
	int arr1[2][3][4];
	double arr2[5][5][5];

	printf("int형배열 크기: %d \n double형 배열크기 : %d \n", sizeof(arr1), sizeof(arr2));
	return 0;

	}
	
```
![3차원2](https://postfiles.pstatic.net/MjAyMDAxMTdfODUg/MDAxNTc5MTkxODA5NTkx.MzL8sRGQXPNdU8a1m2KvMg4kz6GrswuymwfZeYtIfRcg.3yAA9qhIjUQgFqu4bm7kjAYL49QE1n0Mvhow3QSiXzYg.PNG.luckeun0713/int_%EB%8D%94%EB%B8%94%EB%B0%B0%EC%97%B4.PNG?type=w580)
### 3차원 배열의 선언과 접근 
3차원 배열은 2차원 배열이 여러개 모여있는 형태로 이해하는 것이 합리적이다.

int record [3][3][2] ; 은  
int record2[3][2]가 3개 겹쳐져있는 것으로 이해하는 편이 낫다.

![참고](https://postfiles.pstatic.net/MjAyMDAxMTdfNTIg/MDAxNTc5MTkyNjA1MTE5.cAv4cajFxjxXsE-sgVNbTOVb7Z7Pdh5KcyEtNIwF49Ug.F7Yb27sY9yZJQb6ZQ4b6r3tAXtcEvYy1aFlmW9tcWXEg.JPEG.luckeun0713/KakaoTalk_20200117_013100425.jpg?type=w580)

# 수고많으셨습니다~^^
 
 





