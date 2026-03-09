/*Problem: Circular Queue Using Array - Implement using linked list with dynamic memory allocation.

Input:
- First line: integer n (number of elements to enqueue)
- Second line: n space-separated integers
- Third line: integer m (number of dequeue operations)

Output:
- Print queue elements from front to rear after operations, space-separated

Example:
Input:
5
10 20 30 40 50
2

Output:
30 40 50 10 20

Explanation:
Use array and front/rear pointers. Rear wraps around to start after reaching array end. Dequeue removes elements from front. Display remaining elements in correct order.*/
#include <stdio.h>
#include <stdlib.h>

typedef struct {
    int *a;       // dynamic array storage
    int cap;      // capacity
    int front;    // index of current front
    int rear;     // index of current rear
    int size;     // number of elements currently in queue
} CQueue;

CQueue* create_queue(int capacity) {
    CQueue *q = (CQueue *)malloc(sizeof(CQueue));
    if (!q) exit(1);
    q->cap   = (capacity > 0) ? capacity : 1;      // avoid 0-capacity for modulo
    q->a     = (int *)malloc(q->cap * sizeof(int));
    if (!q->a) exit(1);
    q->front = 0;
    q->rear  = -1;
    q->size  = 0;
    return q;
}

int is_full(CQueue *q)  { return q->size == q->cap; }
int is_empty(CQueue *q) { return q->size == 0; }

void enqueue(CQueue *q, int x) {
    if (is_full(q)) return; // for this task, we assume inputs fit; otherwise handle overflow
    q->rear = (q->rear + 1) % q->cap;
