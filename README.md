#include<stdio.h>

#include<math.h>

void main()

{

 int i,j,k,n;
 float a[20][20],c,x[10],sum=0.0;

 printf("\nEnter the order of matrix: ");

 scanf("%d",&n);

 printf("\nEnter the elements of augmented matrix row-wise:\n\n");

 for(i=1; i<=n; i++)

 {

 for(j=1; j<=(n+1); j++)

 {

 printf("a[%d][%d] : ", i,j);

 scanf("%f",&a[i][j]);

 }

 }

 for(j=1; j<=n; j++)

 {

 for(i=1; i<=n; i++)

 {

 if(i>j)

 {

 c=a[i][j]/a[j][j];

 for(k=1; k<=n+1; k++)

 {

 a[i][k]=a[i][k]-c*a[j][k];

 }

 }

 }

 }

 x[n]=a[n][n+1]/a[n][n];

 for(i=n-1; i>=1; i--)
 {
 sum=0;
 for(j=i+1; j<=n; j++)
 {
 sum=sum+a[i][j]*x[j];
 }
 x[i]=(a[i][n+1]-sum)/a[i][i];
 }
 printf("\nThe solution is: \n");
 for(i=1; i<=n; i++)

 {

 printf("\nx%d=%f\t",i,x[i]);

 }

 getch();

 }
 next program
/* Program Newton-Raphson

 Program to find a root of the equation x*x*x - 3x + 1 =0 by

 Newton-Raphson method. f(x) and its derivative fd(x) are to

 be supplies.*/

#include<stdio.h>

#include<math.h>

#include<stdlib.h>

void main()

{

int k=0; //counts number of iterations
float x1,x0; //x0 is the initial guess

float eps=1e-5; //error tolerance

float f(float x);

float fd(float x);

printf("\nEnter the initial guess x0 : ");

scanf("%f",&x0);

x1=x0;

do

{

k++;

x0=x1;

x1=x0-f(x0)/fd(x0);

}

while(fabs(x1-x0)>eps);

printf("One root is %8.5f obtained at %dth iteration",x1,k);

}

//definition of the function f(x)

float f(float x)

{

return(x*x*x-3*x+1);

}

//definition of the function fd(x)

float fd(float x)

{

return(3*x*x-3);

}
next program 
#include<conio.h>

#include<stdio.h>

#include<stdlib.h>

#include<math.h>

int user_power,i=0,cnt=0,flag=0;

int coef[10]={0};

float x1=0,x2=0,t=0;

float fx1=0,fdx1=0;

void main()

{

 printf("\n\n\t\t\t PROGRAM FOR NEWTON RAPHSON GENERAL");

 printf("\n\n\n\tENTER THE TOTAL NO. OF POWER:::: ");

 scanf("%d",&user_power);

 for(i=0;i<=user_power;i++)

 {

 printf("\n\t x^%d::",i);

 scanf("%d",&coef[i]);

 }

 printf("\n");

 printf("\n\t THE POLYNOMIAL IS ::: ");

 for(i=user_power;i>=0;i--)//printing coeff.

 {

 printf(" %dx^%d",coef[i],i);

 }

 printf("\n\tINTIAL X1---->");
 scanf("%f",&x1);

printf("\n******************************************************");

printf("\n ITERATION X1 FX1 F'X1 ");

printf("\n******************************************************");

 do

 {

 cnt++;

 fx1=fdx1=0;

 for(i=user_power;i>=1;i--)

 {

 fx1+=coef[i] * (pow(x1,i)) ;

 }

 fx1+=coef[0];

 for(i=user_power;i>=0;i--)

 {

 fdx1+=coef[i]* (i*pow(x1,(i-1)));

 }

 t=x2;

 x2=(x1-(fx1/fdx1));

 x1=x2;

 printf("\n %d %.3f %.3f %.3f ",cnt,x2,fx1,fdx1);

 }

 while((fabs(t - x1))>=0.0001);

 printf("\n\t THE ROOT OF EQUATION IS %f",x2);

 getch();

}
next program 
#include<stdio.h>

#include<conio.h>

#include<math.h>

float f(float);

float f(float x)

{

 float y;

 y=pow(x,3)+2*x-5;

 return y;
 }

main()

{

int i=0;

float a,b,e,x;

printf("enter the desire accuracy= ");

scanf("%f",&e);

 do

 {

 printf("enter the values of a : ");

 scanf("%f",&a);

 printf("enter the values of b : ");

 scanf("%f",&b);

 }

 while(f(a)*f(b)>0);

 do

 {

 x=a-(b-a)/(f(b)-f(a))*f(a);

 if(f(x)*f(a)>0)

 b=x;

 else

 a=x;

 i=i+1;

 }

 while(fabs(f(x))>e);

 printf("the values of i and x are : %d,%f",i,x);

 getch();

 return 0;

}
next program
/* This program finds the value of integration of a function

 by Trapezoidal rule. Here we assume that f(x) = x^3. */

#include<stdio.h>

#include<conio.h>

#include<math.h>

void main()

{

float a,b,h,sum;

int n,i;

float f(float);

printf("Enter the values of a, b: ");

scanf("%f%f",&a,&b);

printf("Enter the value of n: ");

scanf("%d",&n);

h=(b-a)/n;

sum=(f(a)+f(a+n*h))/2;

for(i=1;i<n;i++)

sum+=f(a+i*h);

sum=sum*h;

printf("The value of the integration is %8.5f: ",sum);

}

float f(float x)

{

return(x*x*x);

}
next program 
/* Program Regula Falsi method 

 Program to find a root of the equation x3-2x-5 */ 



#include<stdio.h>

#include<conio.h>

#include<math.h>

float f(float);

float f(float x){

    float y;

    y = pow(x,3)-2*x-5;

    return y;

}

int main()

{

    int i = 0;

    float a,b,e,x;

    printf("Enter the desired accuracy: ");

    scanf("%f",&e);

    printf("Enter the value of a: ");

    scanf("%f",&a);

    printf("Enter the value of b: ");

    scanf("%f",&b);

    while(f(a)*f(b)<0){

        x=(a*f(b)-b*f(a))/(f(b)-f(a));

        if(f(a)*f(x)<0) b=x;

        else a=x;

        if(fabs(f(x))<e) break;

        i+=1;

    }

    printf("The values of i and x are: %d, %f",i,x);

    getch();

    return 0;

}



