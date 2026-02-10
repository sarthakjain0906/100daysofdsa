/*problem: Read a string and check if it is a palindrome using two-pointer comparison.

Input:
- Single line: string s

Output:
- Print YES if palindrome, otherwise NO

Example:
Input:
level

Output:
YES

Explanation: String reads same forwards and backwards*/
#include <stdio.h>

int main() {
    char s[100];
    int len = 0;

    printf("enter a string:");
    scanf("%s", s);

    while (s[len] != '\0') {
        len++;
    }

    int i = 0, j = len - 1;
    int is_pal = 1;

    while (i < j) {
        if (s[i] != s[j]) {
            is_pal = 0;
            break;
        }
        i++;
        j--;
    }

    if (is_pal)
        printf("YES");
    else
        printf("NO");

    return 0;
}
