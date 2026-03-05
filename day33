/*Problem: Convert an infix expression to postfix notation using stack.

Input:
- Single line: infix expression (operands are single characters)

Output:
- Print the postfix expression

Example:
Input:
A+B*C

Output:
ABC*+

Explanation:
Operator precedence: * > +
Use stack to handle operator precedence and associativity*/
#include <bits/stdc++.h>
using namespace std;

int prec(char op) {
    if (op == '^') return 3;
    if (op == '*' || op == '/') return 2;
    if (op == '+' || op == '-') return 1;
    return 0;
}

bool isRightAssociative(char op) {
    return op == '^';
}

bool isOperand(char c) {
    return isalnum(static_cast<unsigned char>(c));
}

string infixToPostfix(const string& expr) {
    string output;
    stack<char> st;

    for (char ch : expr) {
        if (ch == ' ') continue;

        if (isOperand(ch)) {
            output.push_back(ch);
        } else if (ch == '(') {
            st.push(ch);
        } else if (ch == ')') {
            while (!st.empty() && st.top() != '(') {
                output.push_back(st.top());
                st.pop();
            }
            if (!st.empty() && st.top() == '(') st.pop();
            else throw runtime_error("Mismatched parentheses");
        } else {
            // operator
            while (!st.empty() && st.top() != '(' &&
                   (prec(st.top()) > prec(ch) ||
                    (prec(st.top()) == prec(ch) && !isRightAssociative(ch)))) {
                output.push_back(st.top());
                st.pop();
            }
            st.push(ch);
        }
    }

    while (!st.empty()) {
        if (st.top() == '(' || st.top() == ')')
            throw runtime_error("Mismatched parentheses");
        output.push_back(st.top());
        st.pop();
    }

    return output;
}

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    string expr;
    if (!getline(cin, expr)) return 0;

    try {
        cout << infixToPostfix(expr) << "\n";
    } catch (const exception& e) {
        // For judged problems, usually avoid printing error messages.
        // cerr << "Error: " << e.what() << "\n";
    }
    return 0;
}
