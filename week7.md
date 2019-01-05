
1. 배열을 사용하여 98.56, 78.62, 78.69, 89.32, 95.29를 초기화하여 출력하고 배열의 총합과 평균을 구하여 출력하는 프로그램을 작성하시오.


```
#include <stdio.h>

int main(){
    
    double cal[] = {98.56, 78.62, 78.69, 89.32, 95.29};
    int i,sum=0;
    
    printf("배열 : ");
    for(i=0; i <  ( sizeof(cal) / sizeof(cal[0]) );i++ ){
       sum+=cal[i];
        printf("%.2lf ",cal[0]);
    }
    
    
    
    printf("\n총합 : %.3lf  평균: %.3lf \n",sum,sum/(sizeof(cal)/sizeof(cal[0])));
    
    return 0;
}
```

<br>
2. 달의 말일을 배열 month에 저장하고 년과 달을 표준입력으로 받아 그 해 그 달의 말일을 출력하는 프로그램을 작성하시오.

```
#include <stdio.h>
#define GIL 12

int main(){
    
    int month[GIL] ;
    int year,dal,i;
    
    printf("년을 입력하시오.\n");
    scanf("%d",&year);
    printf("달을 입력하시오.\n");
    scanf("%d",&dal);
    
    
    /*
     * for문을 통하여 반복하고 sitch를 통하여 배열  month에 그 해의 그 달 말일은 저장한다
     */
    for(i=0;i<sizeof(month)/sizeof(month[0]);i++){
        switch (i+1) {
            case 1:// 31일
            case 3:
            case 5:
            case 7:
            case 8:
            case 10:
            case 12:
                 month[i]=31;
                 break;
            case 4:// 30일
            case 6:
            case 9:
            case 11:
                 month[i]=30;
                 break;
            case 2:// 2월 윤달 처리
                 if (year%4==0) {// 4년으로 나뉘는 연도
                    if(year%100==0){// 100년으로 나뉜다면
                        if (year%400==0) {//400년으로 나뉜년도
                             month[i]=29;
                               } else {
                                    month[i]=28;
                               }
                            }else{
                                month[i]=29;;//4년으로 나뉘나 100년으로 나뉘지 않는 연도
                       }
                  } else {// 4년으로 나뉘지 않는 연도
                       month[i]=28;
                }
                break;
            }
    }
    
    
    printf("%d년 %d달의 말일은 %d일 이다.\n",year,dal,month[dal-1]);
    
    
    
    return 0;
}
```

<br>
3. 반복문을 이용하여 다음과 같은 수를 배열에 10개에 순서대로 저장하고 이 값을 출력하는 프로그램을 작성하시오. 
<br>1/(2*3), 1/(3*4), 1/(4*5), …, 1/(11*12)

```
#include <stdio.h>
#define GIL 10

int main(){
    double task[GIL];// 10의 크기를 가진 배열을 선언
    int i;
    
     //배열의 값을 반복문을 통하여 입력 하고 출력한다.
   for(i=0; i<(sizeof(task)/sizeof(task[0]));i++){
     task[i] = 1.0 / ( (i+2) * (i+3) );
     printf("task[%d]= %lf \n",i,task[i]);
  }
    
    
    return 0;
}
```

<br>
4. 
다음 [C 프로그래밍] 점수를 이차원 배열에 저장하고, 각 학생 당 합과 평균을 구하여 출력하는 프로그램을 작성하시오.

```
#include <stdio.h>
#define GIL 4

int main(){
    int score[][GIL] = {{97,90,88,95},{76,89,75,83},{60,70,88,82},{83,89,92,85},{75,73,72,78}};
    double sum[sizeof(score)/sizeof(score[0][0])];
    int i,j;
    
    // 이중 반복문을 통하여 배열을 출력한다.
    printf("학생의 점수\n");
    for(i=0;i<sizeof(score)/sizeof(score[0]);i++){
        for(j=0;j<sizeof(score[0])/sizeof(score[i][0]);j++){
            printf("%d ",score[i][j]);
        }
        printf("\n");
    }
    printf("\n");
    // 이중 반복문을 통하여 계산한다.
    for(i=0;i<sizeof(score)/sizeof(score[0]);i++){
        for(j=0;j<sizeof(score[0])/sizeof(score[i][0]);j++){
            sum[i]+=score[i][j];
        }
        printf("학생%d의 성적 합: %.0lf 평균: %.3lf \n",i+1,sum[i],sum[i]/sizeof(score[i][0]));
    }
    
    
    return 0;
}
```

<br>
5. 
다음 표의 가로 합과 세로 합, 그리고 모든 수의 합을 구하는 프로그램을 작성하시오. 

```
#include <stdio.h>
#define GIL 4

int main(){
    int score[][GIL] = {{78,48,78,98},{99,92,83,29},{29,64,83,89},{34,78,92,56}};
    double sum[sizeof(score)/sizeof(score[0][0])];
    double sum2=0;
    int i,j;
    
    // 이중 반복문을 통하여 합을 계산한다.
    // 그리고 합을 통하여 평균을 계산하여 출력한다.
    printf("원 배열\n");
    for(i=0;i<sizeof(score)/sizeof(score[0]);i++){
        for(j=0;j<sizeof(score[0])/sizeof(score[i][0]);j++){
            printf("%d ",score[i][j]);
        }
        printf("\n");
    }
    
    printf("\n");
    for(i=0;i<sizeof(score)/sizeof(score[0]);i++){
        for(j=0;j<sizeof(score[0])/sizeof(score[i][0]);j++){
            sum[i]+=score[i][j];
        }
        printf("%d행의  합: %.0lf 평균: %.3lf \n",i+1,sum[i],sum[i]/sizeof(score[i][0]));
        sum2+=sum[i];
    }
    
    printf("총합: %0.3lf\n",sum2);
    
    return 0;
}
```

<br>
6. 
다음 4 x 3의 행렬에서 두 행렬의 합과 차를 구하는 프로그램을 작성하시오.
배열에서 같은 첨자의 행과 열에 대응하는 원소의 합과 차를 구하는 연산

```
#include <stdio.h>
#define GIL 3

int main(){
    int fir[][GIL] = {{46,79,78},{35,57,28},{43,68,76},{56,78,96}};
    int sec[][GIL] = {{78,35,99},{85,82,34},{58,69,29},{34,59,35}};
    int hap[sizeof(fir)/sizeof(fir[0])][sizeof(fir)/sizeof(fir[0][0])];
    int cha[sizeof(fir)/sizeof(fir[0])][sizeof(fir)/sizeof(fir[0][0])];
    int i,j;
    
    // 이중 반복문을 통하여 합을 계산한다.
    // 그리고 합을 통하여 평균을 계산하여 출력한다.
    printf("첫번째 배열\n");
    for(i=0;i<sizeof(fir)/sizeof(fir[0]);i++){
        for(j=0;j<sizeof(fir[0])/sizeof(fir[i][0]);j++){
            printf("%d ",fir[i][j]);
        }
        printf("\n");
    }
    printf("\n두번째 배열\n");
    for(i=0;i<sizeof(sec)/sizeof(sec[0]);i++){
        for(j=0;j<sizeof(sec[0])/sizeof(sec[i][0]);j++){
            printf("%d ",sec[i][j]);
        }
        printf("\n");
    }
    
    //계산 밑 합 출력
    printf("\n배열의 합\n");
    for(i=0;i<sizeof(fir)/sizeof(fir[0]);i++){
        for(j=0;j<sizeof(fir[0])/sizeof(fir[i][0]);j++){
            hap[i][j]=fir[i][j]+sec[i][j];
            cha[i][j]=fir[i][j]-sec[i][j];
            printf("%d ",hap[i][j]);
        }
        printf("\n");
    }
    //배열의 차 출력
    printf("\n배열의 차\n");
    for(i=0;i<sizeof(fir)/sizeof(fir[0]);i++){
        for(j=0;j<sizeof(fir[0])/sizeof(fir[i][0]);j++){
            printf("%d ",cha[i][j]);
        }
        printf("\n");
    }

    
    return 0;
}

```

<br>
7. 1부터 50사이의 난수 10개를 생성하여 일차원 배열에 저장한다. 단 중복된 값이 있으면 다시 생성하여 저장한다.

```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#define GIL 10

int main(){
    srand((unsigned)time(NULL));
    int nan[GIL];
    int i,j,falg;
    
    
    // 50가지 난수 만들기
    for(i=0;i<sizeof(nan)/sizeof(nan[0]);i++){
        nan[i]= rand()%50+1;
        falg=i;
        for(j=0;j<i;j++){// 난수가 이전과 겹칠 경우 해당 배열을 다시 생성
            if(nan[j]==nan[i]){
                i--;
                break;
            }
        }
        if(falg==i){// flag와 i가 같지 않다면 같은 수가 입력된 것이므로  출력하지 아니한다.
            printf("[%d]:%d  ",i,nan[i]);
        }
    }
    printf("\n");
    
    return 0;
}
```

<br>
8. 배열 pass에는 2자리수의 정수 난수를 5개 생성하여 배열에 저장한 후 다음과 같이 실행되는 프로그램을 작성하시오.
<br>힌트) 임의 문자 입력 후 화면에 출력된 내용 삭제
<br>      char ch;
<br>      printf(“임의의 문자를 입력하세요”);
<br>ch = getchar();  //문자 입력
<br>system(“cls”);  //화면에 출력된 모든 내용 삭제


```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#define GIL 5

int main(){
    srand((unsigned)time(NULL));
    int pass[GIL];
    int i,j,flag,k;
    char ch;
    
    //  난수 만들기
    printf("두 자리수 난수 생성 :\n\n======난수 출력\n");
    for(i=0;i<sizeof(pass)/sizeof(pass[0]);i++){
        pass[i]= rand()%9+11;
        flag=i;
        
        for(j=0;j<i;j++){
            if(pass[i]==pass[j]){
                i--;
                break;
            }
        }
        if(flag==i){
        printf("[%d ] :    %d\n",i+1,pass[i]);
        }
    }
    printf("\n");
    
    // 임의 문자의 입력받아 출력창을 지운다.
    printf("임의의 문자를 입력하시오.");
    ch = getchar();
    system("cls");//mac에서는 동작 하지 않습니다. 
    
    // 난수 정답 확인
    printf("출력된 화면의 난수 맞추기==>\n");
    flag=0;
    for(i=0;i<sizeof(pass)/sizeof(pass[0]);i++){
        printf("%d 번째 : ",i+1);
        fflush(0);
        scanf("%d",&k);
        if(pass[i]==k){
            flag++;
        }
    }
    
    printf(“\n정답 회수: %d\n",flag);
    
    return 0;
}
```
