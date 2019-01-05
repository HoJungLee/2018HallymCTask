1.구조체 person을 정의하고, 적당한 값을 입력 받아 구조체에 저장하고 출력하는 프로그램을 작성하시오. 
<br>구조체 person 멤버 구성: 이름, 나이, 전화번호

```
#include <stdio.h>
#include <string.h>

struct person{
    char name[10];
    int age;
    char phone[18];
};
;
int main() {
    
    struct person task;
    
    printf("이름을 입력\n”);
    gets(task.name);
    
    
    printf("나이를 입력\n");
    scanf("%d",&task.age);
    
    
    getchar();// 버퍼 비우기
    printf("전화 번호를 입력\n");
    gets(task.phone);
    
    printf("\n이름: %s \n나이: %d \n전화번호: %s\n",task.name,task.age,task.phone);
    
    return 0;
}

```
<br>
2.
다음 내용을 참고로 구조체 professor를 정의하고, 교수 3명을 선언하여 적당한 값으로 초기화 한 후 출력하는 프로그램을 작성하시오. 단, 이름과 나이 전화번호는 1번문제에서 정의된 구조체를 멤버로 사용할 것
<br>

```
#include <stdio.h>
#include <string.h>

struct person{
    char name[10];
    int age;
    char phone[18];
};

typedef struct person PE;

typedef struct{
    char hak[10];
    char dam1[20];
    char dam2[20];
    PE pe;
}Gyo;

int main(){
    Gyo su[3]={ {"전산과","컴퓨터개론","프로그래밍",{"박종학",30,"011-3333-2456"}}, {"교양과","영어회화","국어",{"이종석",30,"016-3467-5469"}} , {"교양과","기초수학","이산수학",{"신용현",30,"017-2222-3344"} } };
 
    int i;
    
    printf("%7s  %3s%15s        %7s  %7s    %7s\n","이름","나이","전화번호","학과","담당","과목");
    
  for(i=0;i<sizeof(su)/sizeof(su[0]);i++){
    printf("%7s %3d %15s %7s %7s %7s\n",su[i].pe.name,su[i].pe.age,su[i].pe.phone,su[i].hak,su[i].dam1,su[i].dam2);
   }
    
    
    return 0;
}

```

<br>
3.다음과 같은 멤버로 구성되는 구조체 Book을 정의한 후 조건대로 처리하는 프로그램을 작성하시오
<br>구성 멤버 : 제목, 저자, 출판사, 페이지수, 가격
<br>구조체를 정의하면서 구조체 type을 재정의 하시오.
<br>적당한 값을 입력 받아 저장한다.

```
#include <stdio.h>

typedef struct {
    char title[12];
    char name[12];
    char puble[12];
    int page;
    int price;
}Book;

int main(){
    
    Book my;
    
    gets(my.name);
    printf("책의 제목:");
    gets(my.title);
    
    printf("책의 저자:");
    gets(my.name);
    
    printf("책의 출판사:");
    gets(my.puble);
    
    printf("책의 페이지 수:");
    scanf("%d",&my.page);
    
    printf("책의 가격:");
    scanf("%d",&my.price);
    
    printf("제목:%s\n저자:%s\n출판사: %s\n페이지:%d \n가격:%d\n",my.title,my.name,my.puble,my.page,my.price);
}

```
