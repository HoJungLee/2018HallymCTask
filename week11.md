1.다음을 참고로 표준입력으로 받은 두 실수의 사칙연산을 수행하는 프로그램을 작성하시오. 
<br>- 사칙연산을 수행하는 함수를 모두 4개 정의하여 이를 함수 포인터 배열에 저장하여 수행
<br>- 사칙연산 중에서 하나의 연산을 다음과 같이 표준입력으로 받음

```
#include <stdio.h>

void add(double *z, double x, double y);
void subtract(double *z, double x, double y);
void multiply(double *z, double x, double y);
void devide(double *z, double x, double y);

int main(){
    int con;
    double x,y,dab;
    double *z=&dab;
    void (*cal[4])(double *,double,double)={add,subtract,multiply,devide};
    
    printf("사칙연산을 위한 각 연산에 대한 번호를 입력하세요, >>\n");
    printf("[더하기]: 0,[빼기]: 1,[곱하기]: 2,[나누기]: 3>>");
    scanf("%d",&con);
    
    printf("\n사칙연산을 수행할 실수 2개를 입력하세요.>>");
    scanf("%lf",&x);
    scanf("%lf",&y);
    
    cal[con](z,x,y);
    
    printf("\n문장 : pfray[%d] 함수 호출 \n",con);
    switch (con) {
        case 0:
            printf("더하기 수행 : %lf + %lf == %lf\n",x,y,*z);
            break;
        case 1:
            printf("빼기  수행 : %lf - %lf == %lf\n",x,y,*z);
            break;
        case 2:
            printf("곱하기 수행 : %lf * %lf == %lf\n",x,y,*z);
            break;
        case 3:
            printf("나누기 수행 : %lf / %lf == %lf\n",x,y,*z);
            break;
    }  
    return 0;
}

void add(double *z, double x, double y){
    *z = x + y;
}
void subtract(double *z, double x, double y){
    *z = x - y;
}
void multiply(double *z, double x, double y){
    *z = x * y;
    
}
void devide(double *z, double x, double y){
    *z = x / y;
}
```

<br>
2.제시된 조건에 따라 함수를 작성한 후 함수 포인터를 이용하여 호출하도록 프로그램 하시오
<br>직원들의 월급이 배열A에 저장되어 있다고 가정하여 회사에서 지급할 월급의 총액을 계산하여 반환하는 함수<br>
          int array_sum(int *A, int size)
<br>
직원들의 월급이 저장된 배열에서 입력된 데이터와 일치하는 급여를 가진 배열의 인덱스를 반환하는 함수, 데이터 입력은 함수에서 받는다
<br>   int array_search(int *A, int size)
<br>
직원들의 월급이 저장된 배열에서 가장 많은 급여를 반환하는 함수
<br>          int array_max(int *A, int size)

```
#include <stdio.h>
#define SIZE 10

//직원들의 월급이 배열A에 저장되어 있다고 가정하여 회사에서 지급할 월급의 총액을 계산하여 반환하는 함수
int array_sum(int *A, int size);

//직원들의 월급이 저장된 배열에서 입력된 데이터와 일치하는 급여를 가진 배열의 인덱스를 반환하는 함수, 데이터 입력은 함수에서 받는다
int array_search(int *A, int size);

//직원들의 월급이 저장된 배열에서 가장 많은 급여를 반환하는 함수
int array_max(int *A, int size);

void printSum(int);
void printFind(int);
void printMax(int);

int main(){
    int pay[SIZE]={100,200,300,400,500,600,700,800,900,999};
    int i,choo;
    int (*fp[3])(int *,int)={array_sum,array_search,array_max};
    void (*pp[3])(int)={printSum,printFind,printMax};
   
    
    for(i=0;i<4;i++){
        printf("1. 급여 총액 2. 급여 찾기 \n3.최고 급여  4. 종료 \n원하는 메뉴를 입력하세요. :");
        scanf("%d",&choo);
        if(choo==4)
            break;
        pp[choo-1](  fp[choo-1](pay,SIZE) );
        printf("\n");
    }
    printf("end\n");
   
    
    
    return 0;
}
// 합계
int array_sum(int *A,int size){
    int sum=0,i;
    for(i=0;i<size;i++){
        sum+=A[i];
    }
    
    return sum;
}
// 인덱스
int array_search(int *A,int size){
    int fin,i;
    printf("검색할 월급을 입력하세요. :");
    scanf("%d",&fin);
    
    for(i=0;i<size;i++){
        if(fin==A[i])
            break;
    }
    
    return i;
}

// max
int array_max(int *A,int size){
    int max=0,i;
    for(i=0;i<size;i++){
        if(max<A[i]){
            max=A[i];
        }
    }
    
    return max;
}
//printSum,printFind,printMax}
void printSum(int x){
    printf("\n급여 총액: %d\n",x);
}

void printFind(int x){
    printf("\n검색 결과(인덱스): %d\n",x);
}

void printMax(int x){
    printf("\n ===급여 찾기===\n최고 급여: %d\n",x);
}
```
<br>
3.1번 문제를 함수 포인터 배열을 이용하여 호출하도록 프로그램을 수정 하시오. 

```
#include <stdio.h>
#define SIZE 10

//직원들의 월급이 배열A에 저장되어 있다고 가정하여 회사에서 지급할 월급의 총액을 계산하여 반환하는 함수
int array_sum(int *A, int size);

//직원들의 월급이 저장된 배열에서 입력된 데이터와 일치하는 급여를 가진 배열의 인덱스를 반환하는 함수, 데이터 입력은 함수에서 받는다
int array_search(int *A, int size);

//직원들의 월급이 저장된 배열에서 가장 많은 급여를 반환하는 함수

 int array_max(int *A, int size);
 
 void printSum(int);
 void printFind(int);
 void printMax(int);
 
 int main(){
 int pay[SIZE]={100,200,300,400,500,600,700,800,900,999};
 int i,choo;
 int (*fp)(int *,int)=NULL;
 void (*pp[3])(int)={printSum,printFind,printMax};
 
 
 for(i=0;i<4;i++){
 printf("1. 급여 총액 2. 급여 찾기 \n3.최고 급여  4. 종료 \n원하는 메뉴를 입력하세요. :");
 scanf("%d",&choo);
 if(choo==1)
     fp=array_sum;
 if(choo==2)
     fp=array_search;
 if(choo==3)
     fp=array_max;
 if(choo==4)
 break;
 pp[choo-1](  fp(pay,SIZE) );
 printf("\n");
 }
 printf("end\n");
 
 
 
 return 0;
 }
 // 합계
 int array_sum(int *A,int size){
 int sum=0,i;
 for(i=0;i<size;i++){
 sum+=A[i];
 }
 
 return sum;
 }
 // 인덱스
 int array_search(int *A,int size){
 int fin,i;
 printf("검색할 월급을 입력하세요. :");
 scanf("%d",&fin);
 
 for(i=0;i<size;i++){
 if(fin==A[i])
 break;
 }
 
 return i;
 }
 
 // max
 int array_max(int *A,int size){
 int max=0,i;
 for(i=0;i<size;i++){
 if(max<A[i]){
 max=A[i];
 }
 }
 
 return max;
 }
 //printSum,printFind,printMax}
 void printSum(int x){
 printf("\n급여 총액: %d\n",x);
 }
 
 void printFind(int x){
 printf("\n검색 결과(인덱스): %d\n",x);
 }
```
