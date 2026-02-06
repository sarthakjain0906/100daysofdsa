/*Problem: Given a sorted array of n integers, remove duplicates in-place. Print only unique elements in order.

Input:
- First line: integer n
- Second line: n space-separated integers (sorted array)

Output:
- Print unique elements only, space-separated

Example:
Input:
6
1 1 2 2 3 3

Output:
1 2 3

Explanation: Keep first occurrence of each element: 1, 2, 3*/
#include <stdio.h>

int main() {
    int n;
    printf("Enter no. of elements: ");
    scanf("%d", &n);

    int arr[n];
    printf("Enter elements: ");
    for(int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    if (n == 0) return 0;

  
    int j = 0; 
    for (int i = 0; i < n - 1; i++) {
       
        if (arr[i] != arr[i+1]) {
            arr[j++] = arr[i];
        }
    }
  
    arr[j++] = arr[n-1];

  
    printf("Result: ");
    for (int i = 0; i < j; i++) {
        printf("%d\t", arr[i]);
    }

    return 0;
}
