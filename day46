/*Problem: Level Order Traversal

Implement the solution for this problem.

Input:
- Input specifications

Output:
- Output specifications*/
#include <stdio.h>
#include <stdlib.h>

// Structure of a tree node
struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

// Create a new node
struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

// Queue implementation for BFS
struct Queue {
    int front, rear, size;
    struct Node** arr;
};

// Create queue of given size
struct Queue* createQueue(int size) {
    struct Queue* q = (struct Queue*)malloc(sizeof(struct Queue));
    q->front = q->rear = -1;
    q->size = size;
    q->arr = (struct Node**)malloc(size * sizeof(struct Node*));
    return q;
}

int isEmpty(struct Queue* q) {
    return q->front == -1;
}

int isFull(struct Queue* q) {
    return q->rear == q->size - 1;
}

void enqueue(struct Queue* q, struct Node* temp) {
    if (isFull(q)) return;

    if (q->front == -1)
        q->front = 0;

    q->arr[++q->rear] = temp;
}

struct Node* dequeue(struct Queue* q) {
    if (isEmpty(q)) return NULL;

    struct Node* temp = q->arr[q->front];

    if (q->front == q->rear)
        q->front = q->rear = -1;
    else
        q->front++;

    return temp;
}

// Level order traversal function
void levelOrder(struct Node* root) {
    if (root == NULL) return;

    struct Queue* q = createQueue(100); // max nodes = 100
    enqueue(q, root);

    while (!isEmpty(q)) {
        struct Node* current = dequeue(q);
        printf("%d ", current->data);

        if (current->left)
            enqueue(q, current->left);

        if (current->right)
            enqueue(q, current->right);
    }
}

// Driver code
int main() {
    struct Node* root = createNode(1);
    root->left = createNode(2);
    root->right = createNode(3);
    root->left->left = createNode(4);
    root->left->right = createNode(5);
    root->right->left = createNode(6);

    printf("Level Order Traversal: ");
    levelOrder(root);

    return 0;
}
