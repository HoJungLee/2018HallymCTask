1.
표준입력으로 두 정수를 입력 받아 합과 평균을 구하여 출력하는 프로그램을 작성하시오. 
<br>합은 정수로, 평균은 실수로 출력

```
#include <stdio.h>
#define CRT SECRURE_NO_WARNINGS

int main() {
    // insert code here...
    int a,b;// 입력 받을 두 정수 저장
    double c;
    
    printf("첫번째 정수 입력\n");
    scanf("%d",&a);
    
    printf("두번째 정수 입력\n");
    scanf("%d",&b);
    
    c=(a+b)/2;
    
    
    printf("입력받은 정수는 %d와 %d% \n 합: %d  평균: %lf\n”, a,b,a+b,c);

    
    return 0;
}

```
<br>
2.
표준입력으로 두 정수를 입력 받아 큰 수를 작은 수로 나눈 몫과 나머지를 각각 출력하는 프로그램을 작성하시오.

```
#include <stdio.h>
#define CRT SECRURE_NO_WARNINGS


int main(){
    // insert code here...
    int a,b,c,d;// 입력 받을 두 정수 저장
    c=0;
    
    printf("첫번째 정수 입력\n");
    scanf("%d",&a);
    
    printf("두번째 정수 입력\n");
    scanf("%d",&b);
    
    printf("입력받은 정수는 %d와 %d%\n",a,b); 
    
    c=a>b?a:b;
	  d=a>b?b:a;
    
    printf("%d에서 %d를 나눈 값:%d \n나머지는 %d\n", c,d,c/d,c%d);

    
    return 0;
}

```

<br>
3.
정수인 천만 이하의 한 수를 입력 받아 우리가 사용하는 단위인 만, 천, 백, 십, 일 단위로 출력하는 프로그램을 작성하시오.
<br>즉 입력이 2347653이면 234만 7천 6백 5십 3입니다. 로 출력
```
#include <stdio.h>
#define CRT SECRURE_NO_WARNINGS


int main(){
    // insert code here...
    int a,b,c,d,e;// 입력 받을 두 정수 저장

    
    printf("천만 이하의 정수 입력\n");
    scanf("%d",&a);
    
    //만
    b=a/10000;
    a%=10000;
    //천
    c=a/1000;
    a%=1000;
    // 백
    d=a/100;
    a%=100;
    // 십
    e=a/10;
    a%=10;
    
    
    printf("입력받은 정수는 %d만 %d천 %d백 %d십 %d입니다. \n",b,c,d,e,a);
    

    
    return 0;
}


```

<br>
2.
표준입력으로 두 정수를 입력 받아 큰 수를 작은 수로 나눈 몫과 나머지를 각각 출력하는 프로그램을 작성하시오.

```
#include <stdio.h>
#define CRT SECRURE_NO_WARNINGS


int main(){
    // insert code here...
    int a,b,c,d;// 입력 받을 두 정수 저장
    c=0;
    
    printf("첫번째 정수 입력\n");
    scanf("%d",&a);
    
    printf("두번째 정수 입력\n");
    scanf("%d",&b);
    
    printf("입력받은 정수는 %d와 %d%\n",a,b); 
    
    c=a>b?a:b;
	  d=a>b?b:a;
    
    printf("%d에서 %d를 나눈 값:%d \n나머지는 %d\n", c,d,c/d,c%d);

    
    return 0;
}

```

<br>
4.
이차원 평면에서 다음 두 점 (3.2, 4.6)와 (-8.3, -2.3)의 중간 지점을 출력하는 프로그램을 작성하시오.  
<br>(X1, Y1)과 (X2, Y2)의 중간지점 = ((X1 + X2)/2, (Y1 + Y2)/2)

```
#include <stdio.h>
#define CRT SECRURE_NO_WARNINGS


int main(){
    // insert code here...
    double a,b,c,d,e,f;// 정수

    
    printf("첫번쨰 x좌표 입력\n");
    scanf("%lf",&a);
    printf("첫번쨰 y좌표 입력\n");
    scanf("%lf",&b);
    printf("두번쨰 x좌표 입력\n");
    scanf("%lf",&c);
    printf("두번쨰 y좌표 입력\n");
    scanf("%lf",&d);
    
    e=(a+c)/2;
    f=(b+d)/2;
    
    

    printf("(%lf,%lf)과  (%lf,%lf)의 중간지점 (%lf,%lf)\n",a,b,c,d,e,f);
    

    
    return 0;
}
```

<br>
5.
지불할 금액을 정수로 입력 받아 화폐단위가 각각 몇 개씩 필요한지 출력하는 프로그램을 작성하시오.
<br>입력은 최소 천원 단위로 입력
<br>화폐단위는 50000, 10000, 5000, 1000 4가지이며, 가능한 큰 화폐단위로 지불 
<br>입력이 236,000이면 50000원권 4개, 10000원권 3개, 5000원권 1개, 1000원권 1개 


```
#include <stdio.h>
#define CRT SECRURE_NO_WARNINGS


int main(){
    // insert code here...
    int a,b,c,d,e;

    
    printf("금액을 입력하시오. (단 최소단위는 1000)\n");
    scanf("%d",&a);
    
    e=a/50000;
    a%=50000;
    b=a/10000;
    a%=10000;
    c=a/5000;
    a%=5000;
    d=a/1000;
    

    printf("입력 받은 금액%d \n오만원권%d개 만원권 %d개 오천원권 %d개 천원권 %d개\n",a,e,b,c,d);
    

    
    return 0;
}

```

<br>
6.
표준입력으로 키와 몸무게를 실수로 입력 받아 다음 조건을 이용하여 정상인지, 비만인지 출력하는 프로그램을 작성하시오.
<br> (몸무게 <= (키 - 100) * 0.9)이면 정상, 아니면 비만

```
#include <stdio.h>
#define CRT SECRURE_NO_WARNINGS

int main() {
	double a,b;

	printf("키를 입력하시오.\n");
	scanf("%lf",&a);
	printf("몸무게를 입력하시오.\n");
	scanf("%lf",&b);

	if(b<(( a - 100)*0.9)){
		printf("정상\n");
	}else{
		printf("비만\n");
	}

    return 0;
}


```

<br>
7.
다음 조건을 만족하는 프로그램을 작성하시오.
<br>원금이 1,000,000인 경우, 예치 기간을 년 단위로 입력 받아 만기 시 총 금액을 출력
<br>년단위 단리이자 = 원금 * 이율(4.5%) * 년(예치기간) 
<br>만기 시 총 수령액(단리적용) = 원금(1 + 이율(4.5%)  * 년(예치기간))

```
#include <stdio.h>
#define CRT SECRURE_NO_WARNINGS

int main() {
	
	int a,b;//  원금,기간
	double c;
	printf("원금을 입력하시오.\n");
	scanf("%d",&a);
	printf("기간을 입력하시오.\n");
	scanf("%d",&b);

	c= a*(1+0.045*b);

	printf("원금:%d\n 기간:%d \n이율 4.5%%(고정) \n만기 시 총 수령액(단리적용)%.0lf\n",a,b,c);

	

    return 0;
}

```
