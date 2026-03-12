/*Implement Heap Sort using a Max Heap to sort an array in ascending order. First build a max heap, then repeatedly extract the maximum element and place it at the end of the array.*/
#include <stdio.h>

// Swap utility
static inline void swap(int *a, int *b) {
    int t = *a; *a = *b; *b = t;
}

/*
 * Heapify the subtree rooted at index i in array a of current size heapSize.
 * Assumes subtrees of children already satisfy max-heap property.
 * Iterative version to avoid recursion overhead.
 */
void heapify(int a[], int heapSize, int i) {
    while (1) {
        int largest = i;
        int left = 2 * i + 1;
        int right = 2 * i + 2;

        if (left < heapSize && a[left] > a[largest]) largest = left;
        if (right < heapSize && a[right] > a[largest]) largest = right;

        if (largest == i) break;

        swap(&a[i], &a[largest]);
        i = largest; // Continue sifting down
    }
}

/*
 * Heap Sort using a max-heap.
 * Sorts the array a of size n in ascending order, in-place.
 */
void heap_sort(int a[], int n) {
    // 1) Build max heap (bottom-up)
    for (int i = n / 2 - 1; i >= 0; --i) {
        heapify(a, n, i);
    }

    // 2) Repeatedly extract max to the end and shrink heap
    for (int end = n - 1; end > 0; --end) {
        swap(&a[0], &a[end]);   // Move current max to end
        heapify(a, end, 0);     // Restore heap on reduced array
    }
}

// Demo
int main(void) {
    int a[] = {12, 11, 13, 5, 6, 7, 7, -2, 0};
    int n = (int)(sizeof(a) / sizeof(a[0]));

    heap_sort(a, n);

    // Print sorted array
    for (int i = 0; i < n; ++i) {
        printf("%d%s", a[i], (i + 1 < n) ? " " : "\n");
    }
    // Expected: -2 0 5 6 7 7 11 12 13
    return 0;
}
``
