/*Problem: Evaluate Postfix Expression - Implement using linked list with dynamic memory allocation.

Input:
- Postfix expression with operands and operators

Output:
- Print the integer result

Example:
Input:
2 3 1 * + 9 -

Output:
-4

Explanation:
Use stack to store operands, apply operators by popping operands, push result back. Final stack top is result.*/
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>
#include <errno.h>

typedef long long i64;

/* --------- Linked-list stack --------- */
typedef struct Node {
    i64 val;
    struct Node *next;
} Node;

static void push(Node **top, i64 v) {
    Node *n = (Node *)malloc(sizeof(Node));
    if (!n) {
        fprintf(stderr, "Memory allocation failed\n");
        exit(EXIT_FAILURE);
    }
    n->val = v;
    n->next = *top;
    *top = n;
}

static int pop(Node **top, i64 *out) {
    if (*top == NULL) return 0;          // underflow
    Node *t = *top;
    *out = t->val;
    *top = t->next;
    free(t);
    return 1;
}

static void free_stack(Node **top) {
    i64 trash;
    while (pop(top, &trash)) { /* free all */ }
}

/* --------- Helpers --------- */
static int is_operator(const char *s) {
    // Single-character operators: + - * /
    return s && strlen(s) == 1 && (s[0] == '+' || s[0] == '-' || s[0] == '*' || s[0] == '/');
}

static int parse_int64(const char *s, i64 *out) {
    // Accept tokens like: 12, -7, +5 (space-separated)
    if (!s || !*s) return 0;
    char *end = NULL;
    errno = 0;
    i64 v = strtoll(s, &end, 10);
    if (errno != 0 || end == s || *end != '\0') return 0;
    *out = v;
    return 1;
}

/* --------- Apply operator --------- */
static int apply_op(char op, i64 a, i64 b, i64 *res) {
    // computes a op b
    switch (op) {
        case '+': *res = a + b; return 1;
        case '-': *res = a - b; return 1;
        case '*': *res = a * b; return 1;
        case '/':
            if (b == 0) return 0;   // divide-by-zero
            *res = a / b;           // integer division (truncates toward zero)
            return 1;
        default:
            return 0;
    }
}

/* --------- Main --------- */
int main(void) {
    char line[8192];      // buffer for one line of postfix input
    if (!fgets(line, sizeof(line), stdin)) {
        // No input
        return 0;
    }

    Node *stack = NULL;

    // Tokenize by whitespace
    for (char *tok = strtok(line, " \t\r\n"); tok != NULL; tok = strtok(NULL, " \t\r\n")) {
        if (is_operator(tok)) {
            // Need two operands: pop b, then a
            i64 b, a, r;
            if (!pop(&stack, &b) || !pop(&stack, &a)) {
                fprintf(stderr, "Error: Stack underflow (too few operands for operator '%s')\n", tok);
                free_stack(&stack);
                return EXIT_FAILURE;
            }
            if (!apply_op(tok[0], a, b, &r)) {
                fprintf(stderr, "Error: Invalid operation or divide by zero\n");
                free_stack(&stack);
                return EXIT_FAILURE;
            }
            push(&stack, r);
        } else {
            // Expect a number (can be negative like -12)
            i64 v;
            if (!parse_int64(tok, &v)) {
                fprintf(stderr, "Error: Invalid token '%s'\n", tok);
                free_stack(&stack);
                return EXIT_FAILURE;
            }
            push(&stack, v);
        }
    }

    // Final result: exactly one value on stack
    i64 result;
    if (!pop(&stack, &result)) {
        fprintf(stderr, "Error: Empty expression or invalid postfix\n");
        free_stack(&stack);
        return EXIT_FAILURE;
    }
    if (stack != NULL) {
        fprintf(stderr, "Error: Extra operands/operators (stack not empty at end)\n");
        free_stack(&stack);
        return EXIT_FAILURE;
    }

    printf("%lld\n", result);
    return 0;
}
``
