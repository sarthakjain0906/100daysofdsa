/*Problem: Implement a stack data structure using an array with the following operations: push, pop, and display.

Input:
- First line: integer n (number of operations)
- Next n lines: operation type and value (if applicable)
  - 1 value: push value
  - 2: pop
  - 3: display

Output:
- For display: print stack elements from top to bottom
- For pop: print popped element or 'Stack Underflow'

Example:
Input:
5
1 10
1 20
3
2
3

Output:
20 10
20
10*/
#include <stdio.h>
#include <stdlib.h>

typedef struct {
    int *data;      // underlying array
    int top;        // index of top element (top == -1 means empty)
    int capacity;   // current allocated capacity
} Stack;

void initStack(Stack *s) {
    s->capacity = 4;                 // start small; will grow as needed
    s->data = (int*)malloc(s->capacity * sizeof(int));
    if (!s->data) {
        fprintf(stderr, "Memory allocation failed\n");
        exit(EXIT_FAILURE);
    }
    s->top = -1;
}

void freeStack(Stack *s) {
    free(s->data);
    s->data = NULL;
    s->capacity = 0;
    s->top = -1;
}

void ensureCapacity(Stack *s) {
    if (s->top + 1 >= s->capacity) {
        int newCap = s->capacity * 2;
        int *newData = (int*)realloc(s->data, newCap * sizeof(int));
        if (!newData) {
            fprintf(stderr, "Memory reallocation failed\n");
            freeStack(s);
            exit(EXIT_FAILURE);
        }
        s->data = newData;
        s->capacity = newCap;
    }
}

void push(Stack *s, int value) {
    ensureCapacity(s);
    s->data[++(s->top)] = value;
}

int pop(Stack *s, int *out) {
    if (s->top == -1) return 0;   // underflow
    *out = s->data[(s->top)--];
    return 1;
}

void display(const Stack *s) {
    if (s->top == -1) {           // empty stack -> print blank line
        printf("\n");
        return;
    }
    for (int i = s->top; i >= 0; --i) {
        printf("%d", s->data[i]);
        if (i != 0) printf(" ");
    }
    printf("\n");
}

int main(void) {
    int n;
    if (scanf("%d", &n) != 1) return 0;

    Stack st;
    initStack(&st);

    for (int i = 0; i < n; ++i) {
        int op;
        if (scanf("%d", &op) != 1) break;

        if (op == 1) {
            int val;
            if (scanf("%d", &val) != 1) break;
            push(&st, val);
        } else if (op == 2) {
            int popped;
            if (pop(&st, &popped)) {
                printf("%d\n", popped);
            } else {
                printf("Stack Underflow\n");
            }
        } else if (op == 3) {
            display(&st);
        } else {
            // Unknown op: ignore or handle as needed
        }
    }

    freeStack(&st);
    return 0;
}
