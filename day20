#include <stdio.h>
#include <stdlib.h>

static int cmp_ll(const void *a, const void *b) {
    long long x = *(const long long*)a;
    long long y = *(const long long*)b;
    if (x < y) return -1;
    if (x > y) return 1;
    return 0;
}

int main(void) {
    int n;
    if (scanf("%d", &n) != 1) return 0;

    long long *a = (long long*)malloc((size_t)n * sizeof(long long));
    if (!a) return 0;

    for (int i = 0; i < n; ++i) {
        if (scanf("%lld", &a[i]) != 1) {
            free(a);
            return 0;
        }
    }

    // Build prefix sums, including an initial 0
    long long *pref = (long long*)malloc((size_t)(n + 1) * sizeof(long long));
    if (!pref) {
        free(a);
        return 0;
    }

    pref[0] = 0;
    for (int i = 0; i < n; ++i) {
        pref[i + 1] = pref[i] + a[i];
    }

    // Sort prefix sums
    qsort(pref, (size_t)(n + 1), sizeof(long long), cmp_ll);

    // Count pairs of equal prefix sums: for each group of size k, add k*(k-1)/2
    long long ans = 0;
    long long run = 1; // current run length of equal values

    for (int i = 1; i <= n; ++i) {
        if (pref[i] == pref[i - 1]) {
            run++;
        } else {
            ans += run * (run - 1) / 2;
            run = 1;
        }
    }
    // Last group
    ans += run * (run - 1) / 2;

    printf("%lld\n", ans);

    free(pref);
    free(a);
    return 0;
}
