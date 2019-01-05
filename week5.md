1.

다음을 참고로 표준입력으로 두 실수 x, y를 이용하여 연산 값을 출력하는 프로그램을 작성하시오.
<br>x: 양수 y: 양수 : x + y
<br>x: 양수 y: 0 또는 음수 : x - y 
<br>x: 0 또는 음수 y: 양수 : -x + y 
<br>x: 0 또는 음수 y: 0 또는 음수 : -x - y  

```
#include <stdio.h>

int main(){
    double x,y;
    
    printf("x를 입력하시오.\n");
    scanf("%lf",&x);
    printf("y를 입력하시오.\n");
    scanf("%lf",&y);
    
    if(x>0){// x가 양수일 때
        if(y>0){//Y도 양수일때
            printf("%lf + %lf = %lf\n",x,y,x+y);
        }else{//Y는 양수가 아닐때
            printf("%lf + %lf = %lf\n",x,y,x-y);
        }
    }else{//x가 0또는 음수일 때
        if(y>0){//Y는 양수일때
            printf("%lf + %lf = %lf\n",x,y,-x+y);
        }else{//Y는 양수가 아닐때
            printf("%lf + %lf = %lf\n",x,y,-x-y);
        }
    }
    
    return 0;
}

```

<br>
2.
다음을 참고로 표준입력으로 받은 월(month)에 해당하는 분기를 출력하는 프로그램을 switch 문을 사용하여 작성하시오. 
<br>1사분기: 1, 2, 3월, 2사분기: 4, 5, 6월, 3사분기: 7, 8, 9월, 4사분기: 10, 11, 12월

```
#include <stdio.h>

int main(){
    int month;
    
    printf("달을 입력하시오.\n");
    scanf("%d",&month);
    
    switch (month) {// 같은 결과를 가지는 3달씩 묶어서 처리
        case 1:
        case 2:
        case 3:
            printf("1사분기\n");
            break;
        case 4:
        case 5:
        case 6:
            printf("2사분기\n");
            break;
        case 7:
        case 8:
        case 9:
            printf("3사분기\n");
            break;
        case 10:
        case 11:
        case 12:
            printf("4사분기\n");
            break;
        default:
            break;
    }
    
    
    return 0;
}

```

<br>
3.
다음을 참고로 표준입력으로 받은 년도의 윤년을 판단하는 프로그램을 if 문을 사용하여 작성하시오.
<br>기원 연수가 4로 나누어 떨어지는 해는 우선 윤년으로 하고, 
<br>1번 중에서 100으로 나누어 떨어지는 해는 평년으로 하며, 
<br>다만 400으로 나누어 떨어지는 해는 윤년으로 정한다

```
#include <stdio.h>

int main(){
    int year;
    
    printf("년을 입력하시오.\n");
    scanf("%d",&year);
    
    if (year%4==0) {// 4년으로 나뉘는 연도
        if(year%100==0){// 100년으로 나뉜다면
            if (year%400==0) {
                printf("윤년이다.\n");
            } else {
                printf("윤년이 아니다.\n");
            }
        }else{
          printf("윤년이다.\n");//4년으로 나뉘나 100년으로 나뉘지 않는 연도
        }
    } else {// 4년으로 나뉘지 않는 연도
        printf("윤년이 아니다.\n");
    }
    
    return 0;
  
}

```

<br>
4.
위 문제를 참고로 표준입력으로 받은 년도와 달을 이용하여 월의 말일을 출력하는 프로그램을 switch 문을 사용하여 작성하시오.

```
#include <stdio.h>

int main(){
    int year;
    int month;
    int day;
    
    printf("년을 입력하시오.\n");
    scanf("%d",&year);
    printf("달을 입력하시오.\n");
    scanf("%d",&month);
    
    
    
    switch (month) {
        case 1:// 31일
        case 3:
        case 5:
        case 7:
        case 8:
        case 10:
        case 12:
            day=31;
            break;
        case 4:// 30일
        case 6:
        case 9:
        case 11:
            day=30;
            break;
        case 2:// 2월 윤달 처리
            if (year%4==0) {// 4년으로 나뉘는 연도
                if(year%100==0){// 100년으로 나뉜다면
                    if (year%400==0) {//400년으로 나뉜년도
                        day=29;
                    } else {
                        day=28;
                    }
                }else{
                    day=29;;//4년으로 나뉘나 100년으로 나뉘지 않는 연도
                }
            } else {// 4년으로 나뉘지 않는 연도
                day=28;
                
            }
            break;
    }
    
     printf("%d년 %d달의 말일은 %d일입니다.\n",year,month,day);
    
    return 0;
}


```

<br>
5.
1에서 100까지의 정수 중에서 2, 3, 5, 7의 배수를 제외한 수를 한 행에 10 개씩 출력하는 프로그램을 작성하시오. 

```
#include <stdio.h>

int main(){
    int i;
    int count=1;// 10개씩 출력하기 위한
    
    for(i=1;i<=100;i++){//1부터 100까지 반복
        if(i%2==0){
            continue;
        }
        if(i%3==0){
            continue;
        }
        if(i%5==0){
            continue;
        }
        if(i%7==0){
            continue;
        }
        printf("%d ",i);
        count++; // 상승
        
        if(count==11){// 10개씩 작성되면 줄넘김
            printf("\n");
            count=1;
        }
        
    }
    printf("\n");
    return 0;
  
}

```

<br>
6.
1부터 100까지 정수 중에서 소수(prime number)를 출력하는 프로그램을 작성하시오.
<br>소수는 약수가 1과 자신 뿐인 수
<br>2에서부터 자기 자신까지 수로 나누어 떨어지지 않는 수


```
#include <stdio.h>

int main(){
    int i;
    int j;
    int count;// 나누어 지는 횟수 확인
    int flag;// flag가 1일 경우 소수가 아니다
    
    for(i=2;i<=100;i++){//2부터 100까지 반복 #
        // 소수 판단 변수 초기화
        flag=0;
        count=0;
        
        for(j=1;j<=i;j++){
            if(i%j==0){//나누어 지는 횟수 확인
                count++;
            }
            if(count==3){
                flag=1;
                break;
            }
        }
        if(flag==0){// 소수 출력
            printf("%d ",i);
        }
        
    }
    printf("\n");
    return 0;
  
}

```

<br>
7.
표준입력으로 입력한 정수에서 각각의 자리에 해당하는 수를 반대로 출력하는 프로그램을 do while 문을 이용하여 작성하시오.


```
#include <stdio.h>

int main(){
    int i;
    // 표준입력으로 입력받음
    printf("정수를 입력하시오\n");
    scanf("%d",&i);
    
    
    do{
        printf("%d ",i%10);// 10으로 나눈 나머지로 1의 자리를 출력한다
        i/=10;// 10으로 나눈 값을 다시 i의 저장한다
    }while(i>0);// i가 0이 될때 까지 반복하기 위한 조건

    
    printf("\n 프로그램 종료\n");
    return 0;
    
}

```

<br>
8.
다음은 우리나라의 소득세율을 나타내고 있다. 표준입력으로 연봉을 입력 받아 세금을 출력하는 프로그램을 작성하시오.
<br>8,800만원 초과: 8,800만원 초과액 * 35% + 이하 세율에 의한 세금(15,920,000)
<br>4,600만원 초과: 4,600만원 초과액 * 24% + 이하 세율에 의한 세금(5,820,000)
<br>1,200만원 초과: 1,200만원 초과액 * 15% + 이하 세율에 의한 세금(720,000)
<br>1,200만원 이하: 6%


```
#include <stdio.h>

int main(){
    int i;
    double j;
    // 표준입력으로 입력받음
    printf("연봉을 입력하시오(단위 만원)\n");
    scanf("%d",&i);
    
    if(i<1200){// 1200만원 미만
        j=i*0.06; 
    }else if(i<4600){// 4600만원 미만
        j=i-1200;
        j=j*0.15+72;
    }else if(i<8800){// 8800만원 미만
        j=i-4600;
        j=j*0.24 + 582;
    }else{//8800만원 초과
        j=i-8800;
        j=j*0.35 + 1592;
    }
    
    printf("연봉 %d만원의 세금은 %.2lf만원 입니다.\n",i,j);
    
    
  
    return 0;
    
}

```


<br>
9.
다음 수식과 내용을 참고로 해당하는 x와 y 값을 출력하는 프로그램을 작성하시오.
<br>y = 3x3 + 2x2 + x + 5, x는 5에서 10사이 0.5씩 증가하도록


```
#include <stdio.h>

int main(){
    double x=5;
    
    for(x;x<=10;x+=0.5){
        printf("x: %.2lf y: %.2lf \n",x,18+x);
    }
  
  
    return 0;
    
}

```


<br>
10.
다음 조건을 만족하는 프로그램을 작성하시오.
<br>원금이 1,000,000인 경우, 예치 기간을 1년에서 10년까지 매년 말에 받을 총 금액을 출력
<br>만기 시 총 수령액(단리적용) = 원금(1 + 이율(4.5%)  * 년(예치기간))


```
#include <stdio.h>
int main(){
    double cash = 1000000;
    int i;
    
    for(i=1; i<11;i++){
        printf("%d년 후 받을 금액 : %.0lf 원\n",i,cash*(1+0.045*i));
    }
    
    return 0;
    
}
```

<br>
11.
1부터 n까지의 합 중에서 10000을 넘지 않는 가장 큰 합과 그 때의 n을 구하는 프로그램을 작성하시오.

```
#include <stdio.h>
int main(){
    int i;
    int j=0; //합을 담을 변수
    
    for(i=1;;i++){ // 무한 반복
        j+=i;
        if(j>10000){ // 합이 10000을 넘을 경우 break
            j-=i; // 10000을 넘었기 때문에 i를 빼 그 전 합으로 만든다
            break;
        }
    }
    printf("1부터 n까지의 합 중에서 10000을 넘지 않는 가장 큰 합과 그 때의 n?\n");
    printf("가장 큰 합은 %d n은 %i\n",j,i-1);//
    
    return 0;
    
}
```

<br>
12.
문자 하나와 온도를 실수형으로 입력 받아, 문자가 F나 f이면 입력 받은 값을 화씨로 간주하여 섭씨로 바꾸고, 입력 받은 문자가 C나 c이면 입력 받은 값을 섭씨로 간주하여 화씨로 바꾸어 결과를 출력하는 프로그램을 작성하시오.
<br>F = (9.0 / 5.0)*C + 32
<br>C = (5.0 / 9.0)*(F – 32)

```

#include <stdio.h>
int main(){
    char cof;
    double num;
   
    printf("C와 F중 하나를 입력하시오.\n");
    scanf("%c/n",&cof);
    printf("온도를 입력하시오.\n");
    scanf("%lf",&num);
    
    if(cof=='c'||cof=='C'){// 입력받은 문자가 c나 C인지 확인
        num=num*9.0/5.0+32;
        cof='F';
    }else{
        num=num*5.0/9.0-32;
        cof='C';
    }
    
    printf("온도는 %.2lf.%C 입니다.\n",num,cof);
    
    return 0;
    
}

```

