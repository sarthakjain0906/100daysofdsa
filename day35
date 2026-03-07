/*Problem: Queue Using Array - Implement using linked list with dynamic memory allocation.

Input:
- First line: integer n (number of elements)
- Second line: n space-separated integers

Output:
- Print queue elements from front to rear, space-separated

Example:
Input:
5
10 20 30 40 50

Output:
10 20 30 40 50

Explanation:
Use array and front/rear pointers. Enqueue inserts at rear, dequeue removes from front. Display from front to rear.*/
#include <stdio.h>
#include <stdlib.h>

/* --------- Node definition --------- */
typedef struct Node {
    int data;
    struct Node *next;
} Node;

/* --------- Queue with front & rear --------- */
typedef struct Queue {
    Node *front;
    Node *rear;
} Queue;

/* Initialize an empty queue */
void initQueue(Queue *q) {
    q->front = q->rear = NULL;
}

/* Check if queue is empty */
int isEmpty(Queue *q) {
    return q->front == NULL;
}

/* Enqueue at rear */
int enqueue(Queue *q, int value) {
    Node *newNode = (Node *)malloc(sizeof(Node));
    if (!newNode) return 0; // allocation failure
    newNode->data = value;
    newNode->next = NULL;

    if (q->rear == NULL) {
        // First element
        q->front = q->rear = newNode;
    } else {
        q->rear->next = newNode;
        q->rear = newNode;
    }
    return 1;
}

/* Dequeue from front (returns 1 if success, 0 if empty) */
int dequeue(Queue *q, int *out) {
    if (isEmpty(q)) return 0;

    Node *tmp = q->front;
    *out = tmp->data;
    q->front = q->front->next;
    if (q->front == NULL) {
        q->rear = NULL;
    }
    free(tmp);
    return 1;
}

/* Display from front to rear (space-separated) */
void displayQueue(Queue *q) {
    Node *cur = q->front;
    int first = 1;
    while (cur) {
        if (!first) printf(" ");
        printf("%d", cur->data);
        first = 0;
        cur = cur->next;
    }
    printf("\n");
}

/* Free all nodes */
void freeQueue(Queue *q) {
    Node *cur = q->front;
    while (cur) {
        Node *next = cur->next;
        free(cur);
        cur = next;
    }
    q->front = q->rear = NULL;
}

int main(void) {
    int n;
    if (scanf("%d", &n) != 1) {
        return 0; // no/invalid input
    }

    Queue q;
    initQueue(&q);

    for (int i = 0; i < n; ++i) {
        int x;
        if (scanf("%d", &x) != 1) {
            // If less numbers than expected, stop early
            break;
        }
        if (!enqueue(&q, x)) {
            // Allocation failure: clean up and exit
            freeQueue(&q);
            return 0;
        }
    }

    displayQueue(&q);
    freeQueue(&q);
    return 0;
}
