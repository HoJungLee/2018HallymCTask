1.이차원 배열에 다음과 같이 저장한 후 출력하시오. 단, 공백으로 표시된 부분은 0으로 저장한다
<br>void init_r(int [][5]) : ‘ㄹ’자로 배열 초기화
<br>void init_t1(int [][5]) : 두 번째 제시된 결과처럼 배열 초기화
<br>void init_t2(int [][5]) : 세 번째 제시된 결과처럼 배열 초기화
<br>void display(int [][5]) : 배열 원소를 출력
<br>void init_value(int dim[][5]) : 배열원소를 0으로 초기화

```
#include <stdio.h>
#define ROW 5
#define COL 5


// 함수 선언
void init_r(int[][COL]);
void init_t1(int[][COL]);
void init_t2(int[][COL]);
void display(int[][COL]);
void init_value(int[][COL]);




int main(){
    int arr[ROW][COL];
    init_value(arr);
    
    printf("\n=====ㄹ로 배열 초기화 후 출력\n");
    init_r(arr);
    display(arr);
    
    printf("\n=====삼각형\n");
    init_value(arr);
    init_t1(arr);
    display(arr);
    
    printf("\n=====삼각형\n");
    init_value(arr);
    init_t2(arr);
    display(arr);
    
    
    return 0;
}

// ㄹ자로 초기화
void init_r(int arr[][COL]){
    int i,j,k=1;
    
    for(i=0;i<COL;i++){// i 는 열 j는 행
        if(i%2!=0){// 2의 배수열
            for(j=ROW-1;j>=0;j--){
                arr[j][i]=k++;
            }
        }else{// 홀수 열
            for(j=0;j<ROW;j++){
                arr[j][i]=k++;
            }
        }
    }
}


// 출력
void display(int arr[][COL]){
    int i,j;
    for(i=0;i<ROW;i++){
        for(j=0;j<COL;j++){
            if(arr[i][j]!=0){
                printf("%3d ",arr[i][j]);
            }else{
                printf("    ");
            }
        }
        printf("\n");
    }
    
}

// 증가식
void init_t1(int arr[][COL]){
    int i,j,k;
    k=1;
    for(i=ROW-1;i>=0;i--){
        for(j=i;j<COL;j++){
            arr[i][j]=k++;
        }
    }

}

// 이것을 t2로
void init_t2(int arr[][COL]){
    int i,j,k;
    k=1;
    
    for(i=0;i<ROW;i++){
        for(j=COL-1-i;j<COL;j++){
            arr[i][j]=k++;
        }
    }
}

// 0으로 초기회
void init_value(int arr[][COL]){
    int i,j;
    for(i=0;i<ROW;i++){
        for(j=0;j<COL;j++){
            arr[i][j]=0;
        }
    }
}

```

2.다음과 같이 일차원 배열의 동등함을 검사하는 함수를 작성하여 결과를 알아보는 프로그램을 작성하시오. 
<br>int isequalarray(int a[], int b[], int n /* 배열 원소 수 */)
<br>배열 a와 b의 배열크기가 모두 n이며 순차적으로 원소 값이 모두 같으면 1을 반환, 아니면 0을 반환하는 함수 

```

#include <stdio.h>
#define COL 5

int isEqualArray(int a[],int b[],int n);
void PV(int a[],int b);

int main(){
    int fir[COL]={1,2,3,4,5};
    int sec[COL]={1,2,3,4,0};

    printf("첫 번쨰 배열:");
    PV(fir, COL);
    printf("두 번쨰 배열:");
    PV(sec, COL);
    
    printf("\n 두 배열은 ");
    if( isEqualArray(fir, sec, COL) ){
        printf("같다\n");
    }else{
        printf("다르다\n");
    }
    
}

int isEqualArray( int fir[],int sec[],int nnn ){
    
    int i;
    
  for(i=0;i<nnn;i++){
    if(fir[i]!=sec[i]){
        return 0;
    }
  }
    
  return 1;
}

void PV(int arr[],int nnn){
    int i;
    for (i=0;i<nnn; i++) {
        printf("[%d]: %1d ",i,arr[i]);
    }
    printf("\n");
}

```
