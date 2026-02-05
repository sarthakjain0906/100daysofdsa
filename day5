#include <stdio.h>
#include <stdlib.h>

int main() {
    int p, q;
    printf("enter no. of element of server1:");
    scanf("%d", &p);
    printf("enter time entries of server1:");
    int *a = malloc(p * sizeof(int));
    for (int i = 0; i < p; i++) scanf("%d", &a[i]);

    prinf("enter no. of element of server2:");
    scanf("%d", &q);
    printf("enter time entries of server2:");
    int *b = malloc(q * sizeof(int));
    for (int i = 0; i < q; i++) scanf("%d", &b[i]);

    int i = 0, j = 0, printed = 0;

    while (i < p && j < q) {
        int v;
        if (a[i] <= b[j]) v = a[i++];
        else v = b[j++];
        if (printed) printf(" %d", v);
        else {
            printf("%d", v);
            printed = 1;
        }
    }

    while (i < p) {
        if (printed) printf(" %d", a[i]);
        else {
            printf("%d", a[i]);
            printed = 1;
        }
        i++;
    }

    while (j < q) {
        if (printed) printf(" %d", b[j]);
        else {
            printf("%d", b[j]);
            printed = 1;
        }
        j++;
    }

    printf("\n");
    free(a);
    free(b);
    return 0;
}
