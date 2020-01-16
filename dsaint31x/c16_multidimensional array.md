C_16 multidimensional array  
윤성우의 열혈c프로그래밍 p.338

#다차원 배열의 이해와 활용
##1차원과 2차원배열의 선언형태
자료형 배열이름[세로길이][가로길이];

int arr1[3]; // 길이가3인 1차원 int배열
int arr2[7][9]; // 세로길이가 7이고 가로길이가 9인 2차원 int배열
int arr3[7][8][9]; // 세로길이가 7이고 가로길이가 8이며 높이가 9인 3차원 int배열

###다차원 배열은 sizeof연산자로 계산하기
<code>
#include <stdio.h>
main(void)
{
int arr1[7];
int arr2[8][9];
int arr3[8][9][10];
printf("길이가 7인 배열크기: %d \n", sizeof(arr1));
printf("세로길이가 8 가로길이가 9 인 배열크기 : %d \n", sizeof(arr2));
printf("세로길이가 8 가로길이가 9 높이가 10인 배열크기 : %d \n",sizeof(arr3));
return 0;
}
