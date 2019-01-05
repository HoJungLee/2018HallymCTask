1. 라이브러리 함수를 사용하지 않고 문자열 길이를 계산하고 토큰으로 분리하는 프로그램을 작성하시오. 문자열은 입력을 받을 것.
<br>힌트) 공백이 포함된 문자열은 gets() 사용, 최대 길이는 100, 공백을 구분자로 사용

```
 #define _CRT_SECURE_NO_WARNINGS
 #include <string.h>
#include <stdio.h>
 int main(void){
     char str[100];
     char *del=" ";
     char* ptoken;
     gets(str);
 
     printf("input string : %s \n", str);
     printf("length : %d \n",strlen(str));
     ptoken = strtok(str, del);
    
     
     while ( ptoken != NULL ){
         printf("%s\n", ptoken);
         ptoken = strtok(NULL, del);
     }


 return 0;}
```
