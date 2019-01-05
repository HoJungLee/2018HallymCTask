1.제시된 문제를 해결하는 프로그램을 작성하시오.
<br>정수형 변수에 사용자가 입력한 정수를 저장하고 포인터를 이용하여 출력하시오.
<br>문자형 변수에 사용자가 입력한 문자를 저장하고 포인터를 이용하여 출력하시오.
<br>정수 배열에 사용자가 입력한 정수 다섯 개를 저장하고 포인터를 이용하여 출력하시오.
<br>문자 배열에 사용자가 입력한 문자 다섯 개를 저장하고 포인터를 이용하여 출력하시오.
<br>3행3열 이차원 실수 배열에 사용자가 입력한 실수를 저장하고 포인터를 이용하여 출력하시오.

```
#include <stdio.h>
#define SIZE 5
#define R 3
#define C 3

int main(void)
{
    void *p;
    int j,i;
    char ch;
    
    int arr[SIZE];
    double arr2[R][C];
    double (*p2)[3]=arr2;
    
     // 정수
    printf("정수 입력:");
    scanf("%d",&j);
    p=&j;
    printf("정수 : %d\n",*(int *)p);
    
    // 문자
    getchar(); // 버퍼 지우기
    printf("문자 입력:");
    scanf("%c",&ch);
    p=&ch;
    printf("문자 : %c\n",*(char *)p);
    
    // 배열
     getchar(); // 버퍼 지우기
     printf("\n1차원 배열 입력\n");
    
    for(i=0;i<SIZE;i++){
        printf("[%d]:",i);
        scanf("%d",&arr[i]);
    }
    p=arr;
   for(i=0;i<SIZE;i++){
        printf("[%d]: %d ",i,*((int *)p+i));
    }
    printf("\n");
    
    // 2차원 배열
     getchar(); // 버퍼 지우기
     printf("\n2차원 배열 입력\n");
    for(i=0;i<R;i++){
        for(j=0;j<C;j++){
            printf("[%d][%d]: ",i,j);
            scanf("%lf",&arr2[i][j]);
        }
    }
    for(i=0;i<R;i++){
        for(j=0;j<C;j++){
            printf("[%d][%d]: %.2lf",i,j,p2[i][j]);
        }
        printf("\n");
    }
    
    
    
    return 0;
}
```

2. 입력 받은 두 개 실수 데이터를 동시에 반환하는 함수를 작성하시오 
 <br>    void read_data(double *d1, double *d2)  //d1, d2에 입력된 값을 저장
 
```
#include <stdio.h>

void read_data(double *,double *);

int main(){
    double zero=0.0;
    double zero1=0.0;
    double *d1=&zero;
    double *d2=&zero1;
    
    read_data(d1, d2);
    printf("d1: %.2lf d2: %.2lf \n",*d1,*d2);
    
    
    return 0;
    
}

void read_data(double *d1,double *d2){
    printf("d1:");
    scanf("%lf",d1);
    getchar();
    printf("d2:");
    scanf("%lf",d2);
    
}
```

<br>
3.
두 개의 데이터를 교환하는 함수를 작성하시오

<br>void swap(int *a, int *b)  //교환 할 데이터를 매개변수 a, b로 받는다

```
#include <stdio.h>

void swap(int *,int *);

int main(){

    int a=4,b=9;
    int *d1=&a;
    int *d2=&b;
    
   
    printf("=== swap 함수 호출 전 =====\n");
    printf("d1: %d d2: %d \n",*d1,*d2);
    
    swap(d1, d2);
    printf("\n=== swap 함수 호출 후 =====\n");
    printf("d1: %d d2: %d \n",*d1,*d2);
    
    return 0;
    
}



void swap(int* a,int* b){
    int d=*a;
    *a=*b;
    *b=d;
    
}
```

<br>
4.
다음을 참고로 배열에서 모든 원소의 값을 모두 n씩 증가시키는 프로그램을 작성하시오.   
<br>배열 int data[] = {3, 21, 35, 57, 24, 82, 8};, n은 표준입력으로 처리
<br>함수 increment()는 배열 p에서 배열크기 size만큼 모든 원소의 값을 모두 n씩 증가
<br>void increment(int *p, int size, int n)
<br>함수 print()는 배열 원소 출력
<br>void print(int *p, int size)

```
#include <stdio.h>

void increment(int *p,int size,int n);
void print(int *p,int size);


int main(){
    int data[]={3,21,35,57,34,82,8};
    int n;
    int size= sizeof(data)/sizeof(int);
    int *p=data;
    
    print(p,size);
    
    printf("\n배열의 각 원소에 더할 정수를 입력하세요.->");
    scanf("%d",&n);
    
    increment(p,size, n);
    print(p,size);
    return 0;
}


void increment(int *p,int size,int n){
    int i =0;
    for(i=0; i<size;i++){
        p[i]+=n;
    }
}

void print(int *p,int size){
    int i =0;
    printf("배열 원소 값을 출력\n");
    
    for(i=0; i<size;i++){
        printf("[%d]: %d ", i,p[i] );
    }
    printf("\n");
}
```

5.다음과 조건을 만족하는 프로그램을 작성하시오.
<br>이차원 배열을 다음 값으로 초기화하여 각각의 원소의 값을 다음 수식과 같이 수정하는 함수를 정의 - A[i][j] = A[i][j] * 10 + 2;
<br>void increment(int (*)[4], int, int);
<br>     12, 30, 82, 54
<br>			43, 51, 32, 47
<br>			30, 42, 41, 69
<br>
<br>이차원 배열 원소를 출력하는 함수
<br>void print(int (*)[4], int, int);

```
#include <stdio.h>
#define R 3
#define C 4

void increment(int (*)[C],int,int );
void print(int (*)[C],int,int);


int main(){
    int data[R][C]={{12,30,82,54},{43,51,32,47},{30,42,41,69}};
    int (*p)[C]=data;
    
    printf("====== 증가 전 배열 원소 ===== \n");
    print(p, R, C);
    
    increment(p, R, C);
    
    printf("\n====== 증가 후 배열 원소 ===== \n");
    print(p, R, C);
    
    return 0;
   
}


void increment(int (*p)[C],int row ,int col){
    int i,j;
    for(i=0; i<row;i++){
        for(j=0;j<col;j++){
            *(*(p+i)+j)=p[i][j]*10+2;
        }
    }
}

void print(int (*p)[C],int row,int col){
    int i,j;
    
    for(i=0; i<row;i++){
        for(j=0;j<col;j++){
            printf("[%d][%d]: %d ", i,j,*(*(p+i)+j) );
        }
       printf("\n");
    }

}
```
<br>
6. 자료유형 double형 1차원 배열을 다음과 같이 초기화하고, 첫 번째 인자인 배열 source을 두 번째 인자인 배열 target에 복사하는 함수를 만들어 결과를 알아보는 프로그램을 작성하시오.
<br>   double ary[5] = {3.12, 5.14, 7.25, 7.48, 5.91};
<br>   copyarray(double *source, double *target, int size);

```
#define SIZE 5
#include <stdio.h>

void copyarray(double *,double *,int);

int main(){
    double ary[SIZE]={3.12,5.14,7.25,7.48,5.91};
    double zero[SIZE];
    double *sou = ary;
    double *tar = zero;
    int i;
    
    printf("함수 실행 전\n");
    for(i=0;i<SIZE;i++){
        printf("[%d]: %.2lf ",i,tar[i]);
    }
    printf("\n");
    
    copyarray(sou, tar, SIZE);
    
    printf("함수 실행 후\n");
    for(i=0;i<SIZE;i++){
        printf("[%d]: %.2lf ",i,tar[i]);
    }
    printf("\n");
    
    return 0;
}

void copyarray(double *source, double *target, int size){
    int i =0;
    
    for(i=0; i< size ;i++){
        target[i]=source[i];
    }
    
}
```
<br>
7.자료유형 double형 1차원 배열에서 가장 큰 값과 가장 작은 값을 찾아 그 값의 차이를 반환하는 함수를 만들어 결과를 알아보는 프로그램을 작성하시오.

```
#include <stdio.h>

void MaxMin(double [],double* ,int);

int main(){
    
    double arr[]={1.2,1.3,1.4,1.5,1.6,1.7,1.8,1.9,2.0};
    int size = sizeof(arr)/sizeof(arr[0]);
    double save[3];
    double *pd=save;
    
    MaxMin(arr, pd,size);
    
    printf("MAX:%.2lf MIN:%.2lf MAX-MIN:%.2lf \n",pd[0],pd[1],pd[2]);
    
    return 0;
    
}

void MaxMin(double arr[],double *dp,int size){
    int i;
    dp[0]=arr[0];
    dp[1]=arr[0];
    for(i=0;i<size;i++){
        
        
        if(dp[0]<arr[i]){
            dp[0]=arr[i];
        }
        if(dp[1]>arr[i]){
            dp[1]=arr[i];
        }
        }
    
    
    dp[2]=dp[0]-dp[1];
    
    
}
```
<br>
8.
다음 내용을 참고로 정수형 배열에 저장되어 있는 정수에서 앞부분 1바이트만을 문자로 변환하여 출력하는 프로그램을 작성하시오.
<br>함수 setarray()는 배열a의 원소에 65부터 1씩 증가하면서 26개의 원소에 정수를 저장하는 함수  void setarray(int *a, int size)
<br>void *인 포인터를 하나 사용하여, 위 함수를 호출하여 얻은 배열 a에서 포인터의 이동은 int *로 하면서, 실제 출력은 1바이트만 문자형으로 출력, 총 출력원소는 26개로 출력결과는 A, B, …, Z까지

```
#include <stdio.h>

void setarray(int *a,int size);

int  main(){
    int arr[26];
    void *ip=arr;
    int size=sizeof(arr)/sizeof(arr[0]);
    int i;
    
    setarray((int *)ip, size);
    
    for(i=0;i<size;i++){
        printf("%C ",*((int *)ip+i));
    }
    printf("\n");
    
    
    
    return 0;
}

void setarray(int *ip,int size){
    int i;
    for(i=65;i<65+size;i++){
        ip[i-65]=i;
    }
    
}
```
