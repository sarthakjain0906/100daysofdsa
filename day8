/*Problem: Given integers a and b, compute a^b using recursion without using pow() function.

Input:
- Two space-separated integers a and b

Output:
- Print a raised to power b

Example:
Input:
2 5

Output:
32

Explanation: 2^5 = 2 * 2 * 2 * 2 * 2 = 32*/
#include<stdio.h>
int power(int,int);
int main()
{   int a,b;
    printf("enter number:");
    scanf("%d",&a);
    printf("enter power:");
    scanf("%d",&b);
    int result = power(a,b);
    printf("%d^%d is %d:",a,b,result);
    return 0;

}
int power(int a,int b)
{   if(b!=0){
    return (a*power(a,b-1));
}
    else
    return 1;
}
