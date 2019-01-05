1.다음 내용을 참고로 구조체 car를 정의하고, 자동차 2대를 선언하여 적당한 값을 입력하고 출력하는 프로그램을 작성하시오.
<br>구조체 car멤버의 구성: 년식, 차종, 등록주인(개인이거나 또는 회사)
<br>구조체 person 멤버 구성: 이름, 전화번호, 주소
<br>등록주인은 공용체를 이용하고 개인인 경우는 위의 구조체 person을 이용하고, 회사인 경우는 회사의 이름으로 입력한다.

```
#include <stdio.h>
#include <string.h>

struct person
{
	char name[20];
	char tel[20];
	char address[80];
};
typedef struct person person;

union reg
{
	person man;
	char company[20];
};
typedef union reg reg;

struct car
{
	char year[10];
	char kind[20];
	reg owner;
};
typedef struct car car;

int main()
{
	car c[3] = { { "2012 08", "그랜져 GT",{ "홍길동","011-1111-1111","서울시 구로구 고척동" } }, { "2016 11", "모닝", "한림대학교" }, {"2018 06", "아토즈", {"둘리","010-2312-9876", "강원도 춘천시"} } };


	printf("%10s%16s%30s\n\n", "년  식", " 종 류 ", "  주 인     ");
	printf("%10s%16s%10s%14s%24s\n", c[0].year, c[0].kind, c[0].owner.man.name, c[0].owner.man.tel, c[0].owner.man.address);
	printf("%10s%16s%30s\n", c[1].year, c[1].kind, c[1].owner.company);
	printf("%10s%16s%10s%14s%24s\n", c[2].year, c[2].kind, c[2].owner.man.name, c[2].owner.man.tel, c[2].owner.man.address);

	return 0;
}

```

<br>
2.다음 내용을 참고로 구조체 employee를 정의하고, 레코드를 수정하고 출력하는 프로그램을 작성하시오.
<br>크기 5인 구조체 배열을 사용하며 입력값으로 초기화한다
<br>구조체 employee 멤버의 구성: 개인정보(구조체 person), 사번, 월급, 연봉
<br>구조체 person 멤버 구성: 이름, 전화번호, 주소
<br>연봉은 월급 * 12 로 계산
<br>입력 받은 사번에 해당하는 레코드를 검색하여 전화번호 또는 주소를 입력 받은 값으로 수정한 후 해당 레코드만 출력
<br>출력 시 연봉을 내림차순으로 출력
<br>전체 레코드 출력은 반드시 함수를 작성하여 처리한다. 이때 구조체 배열을 형식매개변수로 전달하며 포인터로 받도록 한다.
<br>그외 적당한 함수를 작성하여 처리하도록 한다

```
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
typedef struct{
	char name[10];
	char tel[20];
	char addr[80];
}person;
typedef struct{
	person person;
	int p_num;     //사번
	double pay;    //월급
	double salary;  //연봉
} employee;

void emp_print(const employee *, int);  //출력 시 구조체 배열은 참조만 하게 한다
void sort(employee *, int);
void update(employee *, int);

int main(void){
	int size, i;
	employee list[] = {
		{ {"박노해", "011-1452-9875", "서울시 강남구"}, 3478, 2500000, 0},
		{ {"목성균", "010-2278-4851", "대전시 유성구"}, 3489, 4400000, 0},
		{ {"최명희", "010-4851-7615", "광주시 금남동 "}, 3490, 2600000, 0},
		{ {"장일순", "010-8246-7531", "강원도 원주시"}, 3491,  5200000, 0},
		{ {"김훈", "010-9514-7946", "충청남도 청원군"}, 3492, 1200000, 0}
	};

	size = sizeof(list)/sizeof(list[0]);

	for(i=0;i<size;i++)
		list[i].salary = list[i].pay*12;  //연봉 계산

	printf("======== 원본 레코드 출력 =========\n");
	emp_print(list, size);
	sort(list, size);
	printf("\n\n======== 정렬 후 레코드 출력 =========\n");
	emp_print(list, size);
	update(list, size);
	printf("======== 수정 후 레코드 출력 =========\n");
	emp_print(list,size);
	return 0;
}

void update(employee *lp, int size){
	int i, flag=1;
	int num1, num2;
	printf("\n수정하고자 하는 사번을 입력 하세요 : ");
	scanf("%d", &num1);
	for(i = 0; i < size; i ++){
		if((lp+i)->p_num == num1){
			flag=0;
			printf("1:전화번호 수정 \n2:주소 수정\n");
			scanf("%d", &num2);
			fflush(stdin);  //키보드 버퍼를 비운다
			switch(num2){
				case 1:
					printf("새로운 전화번호를 입력하세요:");
//scanf()함수는 공백이 포함된 문자열 처리 불가
         				gets((lp+i)->person.tel);
					break;
				case 2:
					printf("새로운 주소를 입력하세요:");
		     		gets((lp+i)->person.addr);
				    break;
			}
	    }
	}
	if(flag)
		printf("해당 사항 없습니다\n");
}

void sort(employee *lp,int size){
	int max, i, j;
	employee temp;
	for(i=0;i<size-1;i++) {
		max=i;
		for(j=i+1;j<size;j++) {
		   if((lp+max)->salary<(lp+j)->salary)
			   max=j;
		}
		temp=*(lp+i);
		*(lp+i)=*(lp+max);
		*(lp+max)=temp;
	}
}

void emp_print(const employee *lp, int size){
	int i;
	puts("사번   이름      전화번호        주소                월급        연봉");
	for(i = 0; i < size; i++){
		printf("%d   %s   %s    %s  %.1lf  %.1lf\n",
			(lp+i)->p_num, (lp+i)->person.name,(lp+i)->person.tel,
(lp+i)->person.addr, (lp+i)->pay , (lp+i)->salary);
	}
}

```

