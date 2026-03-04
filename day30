/*Problem: Polynomial Using Linked List - Implement using linked list with dynamic memory allocation.

Input:
- First line: integer n (number of terms)
- Next n lines: two integers (coefficient and exponent)

Output:
- Print polynomial in standard form, e.g., 10x^4 + 20x^3 + 30x^2 + 40x + 50

Example:
Input:
5
10 4
20 3
30 2
40 1
50 0

Output:
10x^4 + 20x^3 + 30x^2 + 40x + 50

Explanation:
Each node stores coefficient and exponent. Traverse nodes to print polynomial in decreasing exponent order.*/
#include <stdio.h>
#include <stdlib.h>

typedef struct Node {
    int coeff;            // coefficient
    int exp;              // exponent
    struct Node* next;
} Node;

// Create a new node
Node* createNode(int coeff, int exp) {
    Node* n = (Node*)malloc(sizeof(Node));
    if (!n) {
        fprintf(stderr, "Memory allocation failed\n");
        exit(EXIT_FAILURE);
    }
    n->coeff = coeff;
    n->exp = exp;
    n->next = NULL;
    return n;
}

/*
 * Insert a term into the list in descending order of exponent.
 * If a node with the same exponent exists, their coefficients are added.
 * If the resulting coefficient is 0, the node is removed.
 */
void insertTerm(Node** headRef, int coeff, int exp) {
    if (coeff == 0) return; // ignore zero-coefficient terms

    Node* prev = NULL;
    Node* curr = *headRef;

    // Find insertion point (keep list in descending order of exp)
    while (curr && curr->exp > exp) {
        prev = curr;
        curr = curr->next;
    }

    if (curr && curr->exp == exp) {
        // Combine like terms
        curr->coeff += coeff;
        if (curr->coeff == 0) {
            // Remove node if coefficient becomes zero
            if (prev) prev->next = curr->next;
            else *headRef = curr->next;
            free(curr);
        }
        return;
    }

    // Insert new node between prev and curr
    Node* n = createNode(coeff, exp);
    if (prev == NULL) {
        // Insert at head
        n->next = *headRef;
        *headRef = n;
    } else {
        n->next = curr;
        prev->next = n;
    }
}

// Print polynomial in standard readable form
void printPolynomial(const Node* head) {
    if (!head) {
        printf("0\n");
        return;
    }

    const Node* p = head;
    int firstPrinted = 0; // to manage sign and spaces

    while (p) {
        int c = p->coeff;
        int e = p->exp;

        if (c != 0) {
            // Handle sign and spacing
            if (!firstPrinted) {
                // First term: print sign only if negative
                if (c < 0) printf("-");
            } else {
                // Subsequent terms: print with +/-
                printf(" %c ", (c < 0) ? '-' : '+');
            }

            int absC = (c < 0) ? -c : c;

            // Coefficient & exponent formatting
            if (e == 0) {
                // constant term
                printf("%d", absC);
            } else if (e == 1) {
                // linear term
                if (absC == 1) printf("x");
                else printf("%dx", absC);
            } else {
                // e >= 2
                if (absC == 1) printf("x^%d", e);
                else printf("%dx^%d", absC, e);
            }

            firstPrinted = 1;
        }

        p = p->next;
    }

    if (!firstPrinted) {
        // All coefficients were zero
        printf("0");
    }
    printf("\n");
}

// Free the list
void freeList(Node* head) {
    while (head) {
        Node* tmp = head;
        head = head->next;
        free(tmp);
    }
}

int main(void) {
    int n;
    if (scanf("%d", &n) != 1) {
        fprintf(stderr, "Invalid input for n\n");
        return 1;
    }

    Node* poly = NULL;

    for (int i = 0; i < n; ++i) {
        int coeff, exp;
        if (scanf("%d %d", &coeff, &exp) != 2) {
            fprintf(stderr, "Invalid term at line %d\n", i + 2);
            freeList(poly);
            return 1;
        }
        insertTerm(&poly, coeff, exp);
    }

    printPolynomial(poly);
    freeList(poly);
    return 0;
}
