/*Problem Statement:
Implement a Queue using a linked list supporting enqueue and dequeue operations.

Input Format:
- First line contains integer N
- Next N lines contain queue operations

Output Format:
- Print dequeued elements
- Print -1 if dequeue is attempted on an empty queue*/
#include <bits/stdc++.h>
using namespace std;

struct Node {
    int data;
    Node* next;
    Node(int d) : data(d), next(nullptr) {}
};

class LinkedListQueue {
    Node* head; // front
    Node* tail; // rear
public:
    LinkedListQueue() : head(nullptr), tail(nullptr) {}

    void enqueue(int x) {
        Node* node = new Node(x);
        if (!tail) {
            head = tail = node;
        } else {
            tail->next = node;
            tail = node;
        }
    }

    int dequeue() {
        if (!head) return -1;
        int val = head->data;
        Node* tmp = head;
        head = head->next;
        if (!head) tail = nullptr;
        delete tmp;
        return val;
    }
};

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int N;
    if (!(cin >> N)) return 0;

    LinkedListQueue q;
    string op;
    vector<int> outputs;

    for (int i = 0; i < N; ++i) {
        cin >> op;
        for (auto &c : op) c = tolower(c);
        if (op == "enqueue") {
            int x; 
            if (cin >> x) q.enqueue(x);
        } else if (op == "dequeue") {
            outputs.push_back(q.dequeue());
        } else {
            // unknown op: ignore
        }
    }

    for (int i = 0; i < (int)outputs.size(); ++i) {
        cout << outputs[i] << "\n";
    }
    return 0;
}
``
