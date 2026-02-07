/*Problem: Write a recursive function fib(n) to compute the n-th Fibonacci number where fib(0)=0 and fib(1)=1.

Input:
- Single integer n

Output:
- Print the n-th Fibonacci number

Example:
Input:
6

Output:
8

Explanation: Sequence: 0,1,1,2,3,5,8 at positions 0,1,2,3,4,5,6 */
#include<stdio.h>
#include <stdlib.h>

long long fib(long long n) {
    if (n < 0) {
        fprintf(stderr, "n must be a non-negative integer\n");
        exit(EXIT_FAILURE);
    }
    if (n == 0) return 0;
    if (n == 1) return 1;
    return fib(n - 1) + fib(n - 2);
}

int main(void) {
    long long n;
    printf("enter nth term:");
    if (scanf("%lld", &n) != 1) return 0;
    printf("%lld\n",fib(n));
    return 0;
}
