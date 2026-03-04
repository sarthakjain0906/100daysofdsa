/*Problem: Implement push and pop operations on a stack and verify stack operations.

Input:
- First line: integer n
- Second line: n integers to push
- Third line: integer m (number of pops)

Output:
- Print remaining stack elements from top to bottom

Example:
Input:
5
10 20 30 40 50
2

Output:
30 20 10*/
#include <stdio.h>

int main() {
    int n;
    scanf("%d", &n);

    int stack[n];
    int top = -1;

    // Push n integers
    for (int i = 0; i < n; i++) {
        int x;
        scanf("%d", &x);
        stack[++top] = x;
    }

    // Pop m times
    int m;
    scanf("%d", &m);

    while (m-- > 0 && top >= 0) {
        top--;   // pop
    }

    // Print remaining elements from top to bottom
    for (int i = top; i >= 0; i--) {
        printf("%d", stack[i]);
        if (i > 0) printf(" ");
    }

    return 0;
}
