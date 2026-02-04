/*Problem: Given an array of n integers, reverse the array in-place using two-pointer approach.

Input:
- First line: integer n
- Second line: n space-separated integers

Output:
- Print the reversed array, space-separated

Example:
Input:
5
1 2 3 4 5

Output:
5 4 3 2 1

Explanation: Swap pairs from both ends: (1,5), (2,4), middle 3 stays*/
#include<stdio.h>
int main(){
    int n;
    printf("enter no. of element in the array:");
    scanf("%d",&n);

    int arr1[n];
    printf("enter element seperated by space :");
    for(int i=0;i<n;i++)
    {
        scanf("%d",&arr1[i]);
    }

    int f=0,l=n-1;
    while(f<l)
    {
        int a = arr1[f];
        arr1[f] = arr1[l];
        arr1[l] = a;
        f++;
        l--;
    }
    printf("reversed array is:");
    for(int i=0;i<n;i++)
    {
        printf("%d/t",arr1[i]);
    }
    return 0;
}
