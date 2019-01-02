
## Root finding using Bisection method

f(x)= x3-2x+5=0 <br>
Solution: <br>
a = -2		f(a) = 1<br>
b = -3		f(b) = -16<br>
We know,<br>
x1 = (a+b)/2 =  (-2+(-3))/2  =-2.5 ; f(x1)=(-2.5)3-2(-2.5)+5= -5.625 <br>
x2 = (-2+(-2.5))/2  =-2.25 ; f(x2)=(-2.25)3-2(-2.25)+5= -1.8906 <br>
x3 = (-2+(-2.25))/2  =-2.125 ; f(x3)=(-2.125)3-2(-2.125)+5= -0.3457 <br>
x4= (-2+(-2.125))/2=-2.0625 ; f(x4)=(-2.0625 )3-2(-2.0625 )+5= 0.3513<br>
x5=(-2.0625+(-2.125))/2=-2.0937 ;f(x4)=(-2.0937 )3-2(-2.0937 )+5= 0.008<br>
Root: -2.0937(Ans).<br>

## Bisection method algorithm
Step-1:  Start  <br>
Step-2: Set correct decimal size <br>
Step-3: Set a and b /* a and b for two initial roots <br>
Step-4: Compute: a = f(a) and b= f(b) <br>
 Step-5: If (a & b) > 0 or (a & b) < 0, then display initial roots are wrong. Otherwise continue. <br>
Step-6: xi = (a + b) / 2 <br>
Step-7: f(xi)=(x*x*x-2*x+5)
Step-8: if f(xi) < 0, then compare if(a<0), then set a=xi Otherwise b=xi <br>
Step-9: Else, compare if(a>0), then set a=xi Otherwise b=xi <br>
Step-10: Set m(int)= f(xi) <br>
Step-11: n = m - f(xi) and p = 10*n Set m(int) = p <br>
Step-12: If m==0 then compare size, if equal display success. <br>
Step-13: Else Go to step-6 <br>
Step-14: Exit <br>

## Bisection method flowchart
![bisection-method-solve-with-c-program](https://user-images.githubusercontent.com/15130238/50550077-5fe3c800-0c93-11e9-80a3-6d3aa39b44c7.png)

## Bisection method C program
``` c
#include<stdio.h>
#include<math.h>
main(){
    printf(":::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::");
    printf("\n:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::");
    printf("\n::::::::::::::::::::::: Root finding using Bisection method :::::::::::::::::::::");
    printf("\n:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::");
    printf("\n:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::\n");
    printf("\n  The Equation is: x*x*x-2*x+5=0");
//int equation
int i,j,k,corrtDecimal,size;
float x;
float inputFastRoot,inputSecondRoot;
float fxFastRoot,fxSecondRoot,fxRoots;
printf("\n  How many decimal you want to correct? : ");
scanf("%d",&size);
//First initial Root input Area
printf("a=");
scanf("%f",&inputFastRoot);
x=inputFastRoot;
fxFastRoot=(x*x*x-2*x+5);
printf(" f(a)=%.f",fxFastRoot);
//Second initial Root input Area
printf("\nb=");
scanf("%f",&inputSecondRoot);
x=inputSecondRoot;
fxSecondRoot=(x*x*x-2*x+5);
printf(" f(b)=%.f",fxSecondRoot);
//Check input root and ensure opposite
if(fxFastRoot < 0 &&  fxSecondRoot <0 || fxFastRoot > 0 &&  fxSecondRoot >0){
    printf("\nRoot is not allowed!\nTwo root must be different sign.\n\n");
    exit(0);
}
else{
    printf("\nRoot is allow:");
}
//Start main equation apply
float a,b,tempRoot;
a=inputFastRoot;
b=inputSecondRoot;
for( i=1;i<250;i++){
    x=(a+b)/(float)2;
    printf("\n   X%d=%.6f  ",i,x);
    fxRoots=(x*x*x-2*x+5);
    printf(" f(x%d)=%.6f",i,fxRoots);
    //Compare f(x) negative or positive
    if(fxRoots<0){
            if(fxFastRoot<0){
              a=x;
            }
            else if(fxSecondRoot<0){
                //printf("\nRoot and b is negative");
                b=x;
            }
    }
    else if(fxRoots>0){
        if(fxFastRoot>0){
              //printf("\nRoot and a is positive");
              a=x;
            }
            else if(fxSecondRoot>0){
                //printf("\nRoot and b is positive");
                b=x;
            }
    }
    /* Correct Decimal Area  */
    corrtDecimal=fxRoots;
    tempRoot=fxRoots-corrtDecimal;
    for(k=1; k<size+1; k++){
        tempRoot=10*tempRoot;
            //printf("First octate: %f",tempRoot);
            corrtDecimal=tempRoot;
            //printf("First octate: %d",corrtDecimal);
            if(corrtDecimal ==0){
                if(k==size){
                   printf("\n %d decimal zero.",k);
                    printf(" Root is: %f",x);
                    printf("\n\n");
                   exit(0);
                   }

                corrtDecimal=tempRoot;
                //printf("Root %d",corrtDecimal);
                tempRoot=tempRoot-corrtDecimal;
            }
    }
}
return 0;
}

```
## Output
![bisection-method-solve-with-c-program-output](https://user-images.githubusercontent.com/15130238/50550170-ee0c7e00-0c94-11e9-873e-0eba0d160f19.png)

##
For any kind of information: [fb.com/badrul.me](https://www.facebook.com/badrul.me), hridoyjbd@gamil.com, Skype: hridoyjbd
