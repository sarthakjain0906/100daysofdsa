#include <stdio.h>
#include <stdlib.h>

#define MAX 100005

int adj[MAX][MAX];   // adjacency matrix (not efficient for large N, but simple)
int degree[MAX];     // degree of each node

int main() {
    int n;
    scanf("%d", &n);

    // Initialize degrees
    for (int i = 1; i <= n; i++) {
        degree[i] = 0;
    }

    // Read edges
    for (int i = 0; i < n - 1; i++) {
        int u, v;
        scanf("%d %d", &u, &v);
        degree[u]++;
        degree[v]++;
    }

    // Count leaf nodes
    int leaf_count = 0;
    for (int i = 1; i <= n; i++) {
        if (degree[i] == 1) {
            leaf_count++;
        }
    }

    printf("%d\n", leaf_count);

    return 0;
}
