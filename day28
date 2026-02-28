/*Problem: Circular Linked List Creation and Traversal - Implement using linked list with dynamic memory allocation.

Input:
- First line: integer n
- Second line: n space-separated integers

Output:
- Print the circular linked list elements starting from head, space-separated

Example:
Input:
5
10 20 30 40 50

Output:
10 20 30 40 50

Explanation:
Last node's next points to head. Traverse from head until returning to head to avoid infinite loop.*/
#include <stdio.h>
#include <stdlib.h>

typedef struct Node {
    int data;
    struct Node* next;
} Node;

// Create a new node with given data
Node* createNode(int data) {
    Node* newNode = (Node*)malloc(sizeof(Node));
    if (!newNode) {
        fprintf(stderr, "Memory allocation failed\n");
        exit(EXIT_FAILURE);
    }
    newNode->data = data;
    newNode->next = NULL;
    return newNode;
}

// Build circular linked list from array of values
Node* buildCircularList(int arr[], int n) {
    if (n == 0) return NULL;

    Node* head = createNode(arr[0]);
    Node* tail = head;

    for (int i = 1; i < n; ++i) {
        tail->next = createNode(arr[i]);
        tail = tail->next;
    }
    // Make it circular
    tail->next = head;
    return head;
}

// Print circular list starting from head
void printCircularList(Node* head) {
    if (head == NULL) return;

    Node* curr = head;
    do {
        printf("%d", curr->data);
        curr = curr->next;
        if (curr != head) printf(" ");
    } while (curr != head);
    printf("\n");
}

// Free all nodes in the circular list
void freeCircularList(Node* head) {
    if (!head) return;

    // Break the circle to avoid infinite loop during free
    Node* tail = head;
    while (tail->next != head) {
        tail = tail->next;
    }
    tail->next = NULL;

    // Now free as a normal singly linked list
    Node* curr = head;
    while (curr) {
        Node* tmp = curr;
        curr = curr->next;
        free(tmp);
    }
}

int main(void) {
    int n;
    if (scanf("%d", &n) != 1) {
        fprintf(stderr, "Invalid input for n\n");
        return 1;
    }

    if (n < 0) {
        fprintf(stderr, "n must be non-negative\n");
        return 1;
    }

    int* arr = NULL;
    if (n > 0) {
        arr = (int*)malloc(n * sizeof(int));
        if (!arr) {
            fprintf(stderr, "Memory allocation failed\n");
            return 1;
        }
        for (int i = 0; i < n; ++i) {
            if (scanf("%d", &arr[i]) != 1) {
                fprintf(stderr, "Invalid input for list element\n");
                free(arr);
                return 1;
            }
        }
    }

    Node* head = buildCircularList(arr, n);
    printCircularList(head);
    freeCircularList(head);

    free(arr);
    return 0;
}
