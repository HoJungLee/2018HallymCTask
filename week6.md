1.
두 개의 임의 정수를 m, n을 입력 받아 다음 함수를 작성하여 mn의 결과를 출력하는 프로그램을 작성하시오.
함수 intpow(int m, int n)의 결과는 m의 n승

```
#include <stdio.h>

int intpow(int m , int n);

int main(){
    int m,n;
    printf("정수를 입력하시오.\n");
    scanf("%d",&m);
    printf("몇번 곱하겠습니까?\n");
    scanf("%d",&n);
    
    printf("%d 의 %d승 결과: %d\n",m,n,intpow(m, n));
    
    return 0;
}

int intpow(int m , int n){
    int i;
    int mn=m;
    for( i=1;i<n;i++){
        mn*=m;
    }
    return mn;
}
```

<br>
2.
다음을 참고로 임의의 수의 제곱을 구하는 함수 square()와 세제곱을 구하는 함수 cube()를 구현하여 임의의 수를 입력 받아 다섯 제곱을 구하는 프로그램을 작성하시오. 
<br>cube() 구현 시 square()를 함수 호출하여 이용

```

#include <stdio.h>

int square(int);
int cube(int);

int main(){
    int m;
    
    printf("정수를 입력하시오.\n");
    scanf("%d",&m);

    printf("%d는 5제곱은 %d\n",m,square(m)*cube(m));
    
    return 0;
}


//  제곱
int square(int m){
    int res;
    return res=m*m;
}
// 세제곱
int cube(int m){
    int res;
   return  res=m*(square(m));
}
```

<br>
3.
임의의 양의 정수 n 이 소수인지를 확인할 수 있는 함수를 구현하여, 임의의 수를 입력 받아 소수임을 확인하는 프로그램을 작성하시오

```
#include <stdio.h>

int test(int m);

int main(){
    int m;
    
    printf("정수를 입력하시오.\n");
    scanf("%d",&m);

    printf("%d는(은) 소수",m);
    if(test(m)==1){
        printf("이다.\n");
    }else{
        printf("가 아니다.\n");
    }
  
    
    return 0;
}


//  소수일 경우 1을 소수가 아닐경우 0을 리턴
int test(int m){
    int i;
    int flag=0;
    for(i=2;i<=m;i++){
        if(m%i==0){
            flag++;
        }
        if(flag==2){
            break;
        }
    }
    
        if(flag==1){
            return 1;
        }else{
            return 0;
        }
    
}
```

<br>
4.
다음 식을 참고로 직각 삼각형에서 양변의 길이 a, b가 주어졌을 때 하나의 사선 길이 c를 구하는 함수를 만들고, 
<br>표준입력으로 받은 두 변의 길이 a, b를 이용하여 하나의 사선 길이 c를 구하는 프로그램을 작성하시오.
<br>단, 사선의 길이를 계산하여 반환한다
<br>a^2 + b^2 = c^2

```
#include <stdio.h>

double tri(double , double);

int main(){
    double a;
    double b;
    
    printf("a 길이를 입력하시오.\n");
    scanf("%lf",&a);
    printf("b 길이를 입력하시오.\n");
    scanf("%lf",&b);
    
    printf("%lf^2+%lf^2=%lf\n",a,b,tri(a,b));
    
    return 0;
}


//  c의 길이의 제곱 리턴
double tri(double a,double b){
    return a*a+b*b;
}

```

<br>
5.
한 개의 문자를 매개변수로 받아 대소문자로 변환하여 반환하는 함수를 만들고 이 함수를 이용하여 입력 받은 문자를 대소문자로 변환하는 프로그램을 작성하시오  


```
//
#include <stdio.h>

char deso(char);

int main(){
    char c;
    
    printf("문자를 입력하시오.\n");
    scanf("%c",&c);
    printf("대소문자 변환 결과값은 %c\n",deso(c));
    
    

   
    return 0;
}


//  대소 문자 변환
char deso(char c){
    if(c >= 'a'||c <= 'z'){
        return c-32;
    }
    if(c >='A'|| c <= 'Z'){
        return c+32;
    }
    
    return ' ';
}

```

<br>
6.
함수 absolute()는 실수 하나를 받아들여 절대값을 반환하는 함수를 만들고 입력 받은 실수에 대하여 절대값을 출력하는 프로그램을 작성하시오 

```
#include <stdio.h>

double absolute(double);

int main(){
    double dd;
    
    printf("실수를 입력하시오.\n");
    scanf("%lf",&dd);
    printf("%lf의 절대값은 %lf\n",dd,absolute(dd));
    

   
    return 0;
}


//   절대값 변환
    double absolute(double dd){
    if(dd<0){
        dd*=-1;
    }
    return dd;
}

```

<br>
7.
1에서 n까지 중에서 소수를 출력하는 함수 display를 만들고 테스트하는 프로그램을 작성하시오, 
<br>원형: void display(int n)


```
#include <stdio.h>

void display(int n);

int main(int argc, const char * argv[]) {
    // insert code here...
    int n;
    
    printf("n까지의 소수를 출력하기 위한 n을 입력하시오\n");
    scanf("%d",&n);
    
    display(n);
    
    return 0;
}

void display(int n){
    int i;
    int j;
    int count;// 나누어 지는 횟수 확
    int flag;// flag가 1일 경우 소수가 아니다
    
    for(i=1;i<=n;i++){//1부터 n까지 반복 #
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
}

```

<br>
8.
1부터 n까지의 합을 구하는 함수를 재귀함수로 작성하여, 20을 실인자로 구현한 재귀함수를 한번 호출하여 1부터 20까지 각각의 합이 출력되도록 프로그램을 작성하시오.

```
#include <stdio.h>

int je(int);

int main(){
    int end;
    printf("n까지의 합을 구하기 위한 n을 입력하시오.\n");
    scanf("%d",&end);
    
    printf("%d까지의 합은 %d\n",end,je(end));
    


   
    return 0;
}


// 합을 구하기 위한 재귀함수
int je(int end){
    if(end==1){
        return 1;
    }
    return end+je(end-1);
}

```

<br>
9.
다음 조건이 만족되도록 로또 모의 당첨 프로그램을 작성하시오.
<br>1에서 n까지의 수에서 6개의 난수를 만들어 출력하는 함수 random()을 만들고 테스트 하는 프로그램을 작성하시오. 
<br>단, n은 입력받으며 함수호출시 형식 매개변수로 전달한다. 반환값은 없다 


```
#include <stdio.h>
#include <time.h>//     시간
#include <stdlib.h>// 랜덤


void rotto(int);


int main(){
    
    int end;
    srand((long)time(NULL));
    
    printf("n까지의 난수를 만들기 위한 n을 입력하시오.\n");//6
    scanf("%d",&end);
    
    rotto(end);
    
    printf("\n");
    
    return 0;
}


// 난수 출력
void rotto(int end){
    int i;
    int random;
    
    for(i=0;i<=end;i++){
        random=rand()%end+1;
        printf("%d ",random);
    }
}

```
