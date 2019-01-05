1.다음 내용을 참고로 구조체 human 을 정의하고 5명의 구조체 배열을 선언하면서 초기화 한 후 제시된 조건대로 처리하시오.  
<br>구조체 human 멤버 구성: 이름(char), 주민등록번호(char)
<br>조건1 : 사용자로부터 입력된 이름과 일치하는 이름이 존재하면 주민등록 번호를 출력 한다. – strcmp()
<br>조건2 : 조건1을 수행하면서 남자인지 여자인지를 출력하시오 – 주민등록번호를 사용하여 남/여 구분

```
#include <stdio.h>
#include <string.h>
#define _CRT_SECURE_NO_WARNINGS // mac환경에서는 동작 하지 않는 듯 합니다.

typedef struct{
    char name[20];
    char PN[15];
}human;

int main(){
    int i;
    human per[5]={{"kim","123456-123467"},{"lee","123456-2345678"},{"park","123456-2345678"},{"choi","123456-2345678"},{"song","123456-1345678"}};
    
    char name[20];

    puts("이름을 입력하시오");
    gets(name);
    
    for(i=0;i<5;i++){
        if(!strcmp(per[i].name, name)){
            printf("\n주민번호: %s\n성별:",per[i].PN);
            if(!strcmp("1", &(per[i].PN[7]))){
                printf(" 남성입니다.\n");
            }else{
                printf(" 여성입니다.\n");
            }
        }
    }
    
    return 0;
}
```

2.5사람의 개인정보를 처리하는 프로그램을 제시된 조건대로 작성하시오
<br>조건 1 : PERSON 구조체(이름, 년, 월, 일, 급여)를 정의하여 사용하며 크기가 5인 구조체 배열로 처리한다
<br>조건 2 : 배열초기화 시 input() 함수를 사용한다
<br>조건 3 : 입력된 이름과 같은 레코드를 검색하여 출력한다. 단, 적당한 함수를 만들어 처리하며 매개변수로 배열과 찾고자 하는 이름을 전달한다. 검색한 레코드를 반환한다
<br>조건 4 : 조건 3에서 해당 레코드를 검색하지 못하면 기본값으로 초기화된 구조체를 반환한다. 즉, 문자열은 “”, 숫자는 0으로 초기화

```
/*
 5사람의 개인정보를 처리하는 프로그램을 제시된 조건대로 작성하시오
 조건 1 : PERSON 구조체(이름, 년, 월, 일, 급여)를 정의하여 사용하며 크기가 5인 구조체 배열로 처리한다
 조건 2 : 배열초기화 시 input() 함수를 사용한다
 조건 3 : 입력된 이름과 같은 레코드를 검색하여 출력한다. 단, 적당한 함수를 만들어 처리하며 매개변수로 배열과 찾고자 하는 이름을 전달한다. 검색한 레코드를 반환한다
 조건 4 : 조건 3에서 해당 레코드를 검색하지 못하면 기본값으로 초기화된 구조체를 반환한다. 즉, 문자열은 “”, 숫자는 0으로 초기화
 */

#include <stdio.h>
#include <string.h>


typedef struct{
    char name[20];
    int year;
    int month;
    int day;
    int pay;
}PERSON;

PERSON input(void);// 초기화 입력
PERSON search(PERSON *,char *,int);
void output(PERSON *,int);
void output2(PERSON);

int main(){

    PERSON per[5]={{"kim",0,0,0,0},{"lee",0,0,0,0},{"park",0,0,0,0},{"choi",0,0,0,0},{"ddd",0,0,0,0}};//테스트를 위하여 미리 입력해놓은 값입니다.
    PERSON result;
    char name[20];
    int i;
    int size=sizeof(per)/sizeof(PERSON);

    
    
    

    // 초기화
    puts("=== 구조체 배열 초기화 ===");
    for(i=0;i<size;i++){
        printf("%d번째 레코드:\n",i+1);
        per[i]=input();
    }
    
    puts("\n=== 구조체 배열 출력 ===");
    output(per, size);
    
    puts("=== 구조체 배열 검색 ===");
    puts("검색하고자 하는 이름을 입력하세요.");
    gets(name);
    output2( search(per, name, size) );



    return 0;
}


PERSON search(PERSON *pe,char *name,int end){
    PERSON result={"",0,0,0,0};
    int i=0;
    
    for(i=0;i<end;i++){
        if(!strcmp(name,pe[i].name)){
            result=pe[i];
        }
    }

    return result;
}


void output(PERSON *per,int end){
    int i=0;
    for(i=0;i<end;i++){
        printf("이름:%s   급여: %5d 입사 연도: %d년 %d월 %d일\n" , per[i].name,per[i].pay,per[i].year,per[i].month,per[i].day);
    }
}


PERSON input(){
    PERSON result;
    puts("이름: ");
    gets(result.name);
    printf("연 월 일 :");
    scanf("%d %d %d",&result.year,&result.month,&result.day);
    printf("급여:");
    scanf("%d",&result.pay);
    getchar();
    
    return result;
}

void output2(PERSON per){
    printf("이름:%s   급여: %5d 입사 연도: %d년 %d월 %d일\n" , per.name,per.pay,per.year,per.month,per.day);
}
```

<br>
도서목록을 처리하는 프로그램을 작성하세요
<br>조건1 : 다음과 같은 멤버로 구성되는 구조체를 정의하여 사용할 것
<br>제목(문자열), 저자(문자열), 출판사(문자열), 가격(정수) 
<br>조건2 : 다음과 같은 메뉴로 구성된다
<br>1. 저장   2. 검색   3. 출력   4. 종료
<br>조건3: 각각의 메뉴는 함수를 호출하여 처리한다.
<br>조건4: 검색은 입력 받은 지은이에 해당하는 모든 자료를 출력한다. 만약 일치하는 자료가 없으면 “해당 저자가 없습니다”로 출력
<br>조건5: 출력은 저장된 모든 도서목록을 출력한다.
<br>조건6: 저장은 구조체 배열에 멤버 값을 입력하여 저장한다.
<br>조건7: 배열 크기는 최대100으로 한다.
<br>조건8: “종료”메뉴를 선택할 때까지 반복한다.

```
#include <stdio.h>
#include <string.h>


typedef struct{
    char title[20];
    char author[20];
    char publish[20];
    int price;
}BOOK;

int menu(void);  //메뉴를 선택하여 반환하는 함수
BOOK insert(void);  //입력 받은 값으로 초기화 된 구조체 반환
void search(int, BOOK *);  //검색 결과를 출력, 마지막 구조체가 저장된 인덱스와 배열 전달
void print(int, BOOK *);  //배열에 저장된 모든 구조체 출력, 마지막 구조체가 저장된 인덱스와 배열전달

int main(){
    int index=0;
    BOOK book[100];

    while(1){
        //메뉴선택
        //선택된 메뉴가 4이면 반복문 종료
        //선택된 메뉴에 따른 처리
        
        // 조건2 : 다음과 같은 메뉴로 구성된다
       // 1. 저장   2. 검색   3. 출력   4. 종료
  
        switch ( menu()) {
            case 1:
                book[index]=insert();
                index++;
                break;
            case 2:
                search(index, book);
                getchar();
                break;
            case 3:
                print(index, book);
                getchar();
                break;
            case 4:
                puts("종료\n");
                return 0;
            default:
                break;
            
        }
         getchar();
        
    }
}
    //선택된 메뉴를 반환하는 함수 – 본인작성
    int menu(){
        int select=0;
        puts("메뉴를 선택하시오.");
        puts("1. 저장   2. 검색   3. 출력   4. 종료");
        scanf("%d",&select);
        return select;
    }
    
    //입력 받은 값으로 초기화 된 구조체 반환 – 본인작성
    BOOK insert(){
        BOOK input;
        getchar();
        puts("책의 가격을 입력하시오.");
        scanf("%d",&input.price);
        
        getchar();
        
        puts("책의 제목을 입력하시오.");
        gets(input.title);
        
        puts("책의 저자를 입력하시오.");
        gets(input.author);
        
        puts("책의 출판사를 입력하시오.");
        gets(input.publish);
        
        return input;
    }

    // 마지막 구조체가 저장된 인덱스와 배열을 매개변수로 받아 검색결과 출력 – 본인작성
    void search(int count, BOOK *lp){
        char name[20];
        int i=0;
        
        getchar();
        printf("검색할 책의 제목을 입력하세요:\n");
        gets(name);
        //일치하는 내용을 찾아 출력
        
        for(i=0;i<count;i++){
            if( !strcmp( lp[i].title , name ) ){
                printf("제목:%s\n",lp[i].title);
                printf("저자:%s\n",lp[i].author);
                printf("출판사:%s\n",lp[i].publish);
                printf("가격:%d\n",lp[i].price);
            }
        }
    }


    //구조체 배열 출력-본인작성
    void print(int count, BOOK *lp){
         int i=0;
        for(i=0;i<count;i++){
                printf("제목:%s\n",lp[i].title);
                printf("저자:%s\n",lp[i].author);
                printf("출판사:%s\n",lp[i].publish);
                printf("가격:%d\n",lp[i].price);
        }
    }

```
