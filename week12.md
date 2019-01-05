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
<br>

2. 한 단어를 표준입력으로 입력 받아 각각의 단어를 구성하는 문자를 역순으로 출력하는 프로그램을 작성하시오.

```
#include <string.h>
#include <stdio.h>
int main(void){
    char str[100];
    int i=0;
    
    printf("한 단어를 입력하세요.->");
     scanf("%s",str);
    printf("입력한 단어를 반대로 출력합니다. ->");
    
    for(i=strlen(str)-1;i>=0;i-- ){
        printf("%c",str[i]);
    }
    puts(" ");
    
    
    
    return 0;}
```
<br>
3.문자를 하나 입력 받아 아스키 코드 값을 출력하는 프로그램을 작성하시오.

```
#include <stdio.h>
int main(void){
    char *s;
    
    printf("한 문자를 입력하세요.->");
    scanf("%c",s);
    printf("%d",*s);
    
   
    puts(" ");
    
    
    
    return 0;}
```
<br>
4.한 줄의 문자열을 표준입력으로 입력 받아 단어의 문자를 역순으로 출력하는 프로그램을 작성하시오.

```
[프로그램 소스]
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
int main(void){
    char str[100];
    int i=0;
    gets(str);
    printf("한 문장을 입력하세요.->\n");
    gets(str);
    printf("입력한 단어를 반대로 출력합니다. ->\n");
    
    for(i=strlen(str)-1;i>=0;i-- ){
        printf("%c",str[i]);
    }
    puts(" ");
    
    
    
    return 0;}
```

<br>
5.여러 줄의 문자열을 표준입력으로 입력 받아 구두점의 수를 구하여 출력하는 프로그램을 작성하시오.
구두점인지는 함수 ispunct(char)를 사용하여 판단
여러 줄의 문자열 입력
<br>
<br>char line[10][LINENUM];
<br>int maxline = 0, i=0;
<br>
<br>while (gets(line[i++])) {
<br>		maxline++;
<br>}

```
#include <stdio.h>
#include <string.h>

#define LINENUMBER 100
int main(){
    char line[10][LINENUMBER];
    int maxline = 0, i=0,j=0,k=1;
    
    printf("여러 줄에 원하는 문장을 입력하세요. 입력아 다 되었으면\n새로운 줄 청음에 ctrl+z,그리고 Enter를 입력하세요.\n");
    
   
    while(gets(line[i++])){
     maxline++;
    }
 

    for(i=0;i<maxline;i++){
        printf("<< %d 줄에 입력한 문자열에서 구두점 출력 >>\n",i+1);
        for(j=0;j<LINENUMBER;j++){
            if(ispunct(line[i][j])){
                printf("구두점 %d : \n",k);
                k++;
            }
            if(line[i][j]==NULL && line[i][j+1]==NULL){
                break;
            }
        }
    }
    
    return 0;
}
```
<br>
6.다음 내용을 참고로, 정수 형태의 문자열을 정수로 반환하는 함수를 구현하고 결과를 알아보는 프로그램을 작성하시오.
<br>문자열 ”4356”은 정수 4356으로, 다음 두 함수에 대하여 모두 출력
<br>라이브러리 함수 atoi()를 사용해 출력, 함수 atoi()의 함수원형은 stdlib.h에 정의되어 있으며 문자열 str을 정수로 변환하는 함수 
<br>int atoi(const char *str);
<br>직접 구현한 함수 toint()도 사용하여 다음과 같이 출력 
<br>int toint(const char *str);

```
[프로그램 소스]
#include <stdlib.h>
#include <string.h>

int jung(char*);

int main(){
    char str[40];
    printf("정수 하나를 입력하세요.->");
    gets(str);
    
    printf("\n먼저 함수 atoi를 이용한 정수 -> %d\n", atoi(str) );
    printf("직접 구현한 함수를 이용한 정수 -> %d\n", jung(str) );
    return 0;
}

int jung( char *p){
    int i,j=1,res=0;
    
    for(i=strlen(p)-1;i>=0;i--){
        res+=(p[i]-48)*j;// 아스키 코드에서 숫자를 이용
        j*=10;
    }
    
    return res;
}
```

<br>
7.한 줄의 문자열을 표준입력으로 입력 받아 영문자의 대문자는 소문자로, 소문자는 대문자로 변환하여 출력하는 프로그램을 작성하시오.
<br>함수 tolower()와 toupper()를 이용

```
#define _CRT_SECURE_NO_WARNINGS
#include <string.h>
#include <ctype.h>
#include <stdio.h>

int main(void)
{
    char str[100];
    int i;
 
    printf("영어 문장을 입혁하세여요->\n");
    gets(str);

    
    printf("위에서 입력한 문자열에서 대문자와 소문자를 반대로 변환하면 ->\n");
    for(i=0;i<strlen(str);i++){
        if(str[i]<91){
            str[i]=tolower(str[i]);
        }else{
            str[i]=toupper(str[i]);
        }
    }
    printf("%s\n",str);
    
    
    return 0;
}
```

<br>
8.다음 내용을 참고로 여러 줄에 걸쳐 문장을 입력 받아 줄마다 입력된 문자열에서 모든 단어를 추출해 각각의 단어의 길이를 출력하는 프로그램을 작성하시오. 
<br>10줄 이하의 여러 줄에 원하는 문장을 입력하고, 입력이 다 되었으면 새로운 줄 처음에 키 ctrl+Z, 그리고 Enter 키를 입력하면 결과가 출력되도록 한다.
<br>토큰은 빈칸, 쉼표(,), 마침표(.), 느낌표(!) 그리고 탭(\t)으로 구분되는 단어로 길이와 토큰 문자열을 출력한다.

```
[프로그램 소스]
// 프로그램밍 과제 8
#include <stdio.h>
#include <string.h>

#define LINENUMBER 100

int main(){
    char line[10][LINENUMBER];
    int maxline = 0, i=0,j=0,k=1;
    char *ptoken[100];
    char *del =" ";
    
    printf("여러 줄에 원하는 문장을 입력하세요. 입력아 다 되었으면\n새로운 줄 청음에 ctrl+z,그리고 Enter를 입력하세요.\n");
    
    // mac에서 동작 하지 않아서 for 문으로 대체 합니다.
    while(gets(line[i++])){
     maxline++;
    }
   
    for(i=0;i<maxline;i++){
        printf("\n<< %d 줄에 입력한 단어(토큰) 출력 >> \n",i+1);
        ptoken[i] = strtok(line[i], del);
       
        while(ptoken[i] != NULL){
            printf("strlen( %s ) = %d\n",ptoken[i],strlen(ptoken[i]));
            ptoken[i] = strtok(NULL, del);
        }
    }    
    return 0;
}
```
<br>
9.여러 줄의 문자열을 표준입력으로 입력 받아 각 단어가 몇 번 나타났는지 출현 빈도를 출력하는 프로그램을 작성하시오.

```
#include <stdio.h>
#include <string.h>

#define LINENUMBER 100

int main(){
    char line[10][LINENUMBER];
    int maxline = 0, i=0,j=0,k=0,count=0;
    char *ptoken[10];
    char *del = " ";
    char *poken[50];
    int cou[50];
    
    printf("여러 줄에 원하는 문장을 입력하세요. 입력아 다 되었으면\n새로운 줄 처음에 ctrl+z,그리고 Enter를 입력하세요.\n");
    
    
    while(gets(line[i++])){
        maxline++;
    }
    
    for(i=0;i<maxline;i++){
        printf("\n<< %d 줄에 입력한 단어(토큰) 출력 >> \n",i+1);
        ptoken[i] = strtok(line[i], del);
        while(ptoken[i] != NULL){
            printf("%s  ",ptoken[i]);
             poken[j] = ptoken[i];
            ptoken[i] = strtok(NULL, del);
            j++;
        }
    }
    

    // 중복 제거 및 반복 횟수 확인
    for(i=0; i<j ; i++){
        
        for(k=0;k<j; k++){
            if(strcmp(poken[i], poken[k]) == 0){
                if(strcmp(poken[i], del)==0)
                    continue;
                if(count>=1){
                    poken[k]=del;
                   // printf("중복값제거\n");
                }
                count++;
              //  printf(" 갯수 확인\n");
            }
          //   printf("다음k 확인\n");
        }
        
        cou[i]=count;
        count=0;
    //    printf("\n다음i 확인\n");
    }
    
    // 전체 객수 확인
    for(i=0; i < j ; i++){
        if( strcmp(poken[i],del) != 0){
            count++;
        }
    }
   
    printf("새로운 단어에 갯수는 %d 입니다. \n",count);
    
    for(i=0; i < j ; i++){
        if( strcmp(poken[i],del) != 0 ){
            printf("단어 %10s  : %d\n",poken[i],cou[i]);
        }
    }
    
    
    return 0;
}
```

