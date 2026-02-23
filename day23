/*Problem: Merge Two Sorted Linked Lists - Implement using linked list with dynamic memory allocation.

Input:
- First line: integer n
- Second line: n space-separated integers (first list)
- Third line: integer m
- Fourth line: m space-separated integers (second list)

Output:
- Print the merged linked list elements, space-separated

Example:
Input:
5
10 20 30 40 50
4
15 25 35 45

Output:
10 15 20 25 30 35 40 45 50

Explanation:
Compare nodes of both lists, append smaller to result, continue until all nodes are merged.*/
#include <stdio.h>
#include <stdlib.h>

/* Node definition */
typedef struct Node {
    int data;
    struct Node* next;
} Node;

/* Create a new node with given value */
Node* newNode(int val) {
    Node* n = (Node*)malloc(sizeof(Node));
    if (!n) {
        fprintf(stderr, "Memory allocation failed\n");
        exit(EXIT_FAILURE);
    }
    n->data = val;
    n->next = NULL;
    return n;
}

/* Append a node with value 'val' at the tail (maintains head & tail) */
void appendTail(Node** head, Node** tail, int val) {
    Node* n = newNode(val);
    if (*head == NULL) {
        *head = *tail = n;
    } else {
        (*tail)->next = n;
        *tail = n;
    }
}

/* Merge two sorted linked lists and return head of merged list */
Node* mergeSorted(Node* a, Node* b) {
    Node dummy;  /* dummy node to simplify edge cases */
    dummy.next = NULL;
    Node* tail = &dummy;

    while (a != NULL && b != NULL) {
        if (a->data <= b->data) {
            tail->next = a;
            a = a->next;
        } else {
            tail->next = b;
            b = b->next;
        }
        tail = tail->next;
    }

    /* Append the remaining nodes (one of a or b is NULL) */
    tail->next = (a != NULL) ? a : b;

    return dummy.next;
}

/* Print list elements space-separated */
void printList(Node* head) {
    for (Node* cur = head; cur != NULL; cur = cur->next) {
        printf("%d", cur->data);
        if (cur->next) printf(" ");
    }
    printf("\n");
}

/* Free the entire list */
void freeList(Node* head) {
    while (head) {
        Node* tmp = head;
        head = head->next;
        free(tmp);
    }
}

int main(void) {
    int n, m, x;

    /* Read first list */
    if (scanf("%d", &n) != 1) return 0;
    Node *head1 = NULL, *tail1 = NULL;
    for (int i = 0; i < n; i++) {
        if (scanf("%d", &x) != 1) return 0;
        appendTail(&head1, &tail1, x);
    }

    /* Read second list */
    if (scanf("%d", &m) != 1) return 0;
    Node *head2 = NULL, *tail2 = NULL;
    for (int i = 0; i < m; i++) {
        if (scanf("%d", &x) != 1) return 0;
        appendTail(&head2, &tail2, x);
    }

    /* Merge, print, and free */
    Node* merged = mergeSorted(head1, head2);
    printList(merged);
    freeList(merged);

    return 0;
}
