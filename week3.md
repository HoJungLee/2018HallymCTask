1.
다음 조건을 만족하는 프로그램을 작성하시오.
원의 반지름을 표준입력으로 처리
면적공식: 반지름 * 반지름 * 3.14(원주율)
둘레공식: 2 * 3.14(원주율) * 반지름 
```
#define PI 3.14

int main(void) 
{
	double r1;

	printf("반지름을 입력하시오. \n");
	scanf("%lf", &r1);
	printf("면적 : %f \n둘레 : %f \n", r1 * r1 * PI, 2 * PI*r1);

	return 0;
}

```
<br>
2.
다음 조건을 만족하는 프로그램을 작성하시오.
표준입력으로 섭씨온도를 소수로 입력 받아 화씨온도를 소수 4째 자리까지 출력
화씨온도 = (9.0 / 5.0) * 섭씨온도 + 32.0
```
#include <stdio.h>

int main(void) 
{
	double hot;

	printf("섭씨온도를 입력하시오 . \n");
	scanf("%lf", &hot);
	printf("섭씨온도 %.4f 는 화씨온도 %.4f \n", hot, (9.0)/(5.0)*hot + 32.0);

	return 0;
}

```
<br>
3.
다음 조건을 만족하는 프로그램을 작성하시오.
아파트 면적의 평을 표준입력으로 받아 제곱미터(m2)로 출력
1평 3.305785 제곱미터는 define 전처리 지시자를 사용하시오.
```
#include <stdio.h>
#define PY 3.305785

int main(void) 
{
	double m2;

	printf("아파트 면적을 평으로 입력하시오 . \n");
	scanf("%lf", &m2);
	printf("%f 평은  %f 제곱미터이다 \n", m2, m2 * PY);
	return 0;
}

```

<br>
4.
 다음 조건을 만족하는 프로그램을 작성하시오.
길이 km를 표준입력으로 받아 마일(mile)로 출력 
1km는 0.621371마일(mile), const 키워드를 사용하여 상수로 선언
```
#include <stdio.h>

int main(void) 
{
	double km;
	const double MILE = 0.621371;

	printf("속도(km)를 입력하시오 . \n");
	scanf("%lf", &km);
	printf("%f km는  %f 마일이다 \n", km, km * MILE);
	return 0;
}

```

<br>
5.
다음 조건을 만족하는 프로그램을 작성하시오. 출력 결과의 이유를 설명하시오.
문자형 연산 ‘A’ + 2 결과를 문자로 출력 
문자형 연산 ‘A’ + 2 결과를 정수로 출력

```
#include <stdio.h>

int main(void) 
{
	char a='A';


	printf("\'%c\'+ 2 는 문자로 %c \n", a, a+2);
	printf("\'%c\'+ 2 는 정수로 %d \n", a, a+2);
	return 0;
}

```

<br>
6.
표준입력으로 문자를 하나 입력 받아 다음 조건을 만족하는 프로그램을 작성하시오.
입력된 문자, 8진수 코드 값, 10진수 코드 값, 16진수 코드 값 출력

```
#include <stdio.h>

int main(void) 
{
	char c;

	printf("문자를 입력하시오\n");
	scanf("%c",&c);
	printf("문자 %c 는\n", c);
	printf("10진수: %d\n", c);
	printf("8진수: %o \n", c);
	printf("16진수 : %x \n", c);

	return 0;
}

```

<br>
7.
시스템에서 사용하는 자료형(char, short, int, float, double)의 크기를 바이트로 출력하는 프로그램을 작성하시오.

```
#include <stdio.h>

int main(void) 
{	

	printf("char  은 %d byte \n",sizeof(char) );
	printf("short 는 %d byte \n",sizeof(short) );
	printf("float 는 %d byte \n",sizeof(float) );
	printf("int   는 %d byte \n",sizeof(int) );
	printf("double은 %d byte \n",sizeof(double) );

	return 0;
}
```
<br>
8.
제시된 결과처럼 출력되는 프로그램을 작성하시오.
실수 출력 전체 폭 12, 소수이하 3자리
문자 출력 전체 폭 10

```
#include <stdio.h>

int main(void) 
{	
	double d1,d2;
	char c1;
	int i1,i2;
	printf("두개의 실수를 입력하세요. : ");
	scanf("%lf %lf", &d1 , &d2);
	fflush(stdin);
	printf("문자를 입력하세요. : ");
	scanf("%c",&c1);
	printf("입려된 문자(16진) : %x \n",c1);
	printf("입력된 문자(8진수) :%o \n",c1);
	printf("입력된 문자(10진수) :%d \n" ,c1);
	printf("첫번째 실수 : %.3f \n" , d1 );
	printf("두번째 실수 : %e \n" , d2 );
	printf("두개의 정수 데이터 입력(단, 16진수로 입력)");
	
	scanf("%i %i",&i1,&i2);
	printf("%#x & %#x = %#x \n" , i1,i2,i1 & i2 );
	printf("%#x ^ %#x = %#x \n" , i1 , i2 , i1^i2 );

}
```








