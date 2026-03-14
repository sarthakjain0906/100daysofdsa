/*Problem Statement:
Given a queue of integers, reverse the queue using a stack.

Input Format:
- First line contains integer N
- Second line contains N space-separated integers

Output Format:
- Print the reversed queue

Example:
Input:
5
10 20 30 40 50

Output:
50 40 30 20 10*/
#include <bits/stdc++.h>
using namespace std;

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int N;
    if (!(cin >> N)) return 0;

    queue<int> q;
    for (int i = 0; i < N; ++i) {
        int x; cin >> x;
        q.push(x);
    }

    stack<int> st;
    // Move all elements from queue to stack
    while (!q.empty()) {
        st.push(q.front());
        q.pop();
    }
    // Move back from stack to queue (reversed order)
    while (!st.empty()) {
        q.push(st.top());
        st.pop();
    }

    // Print the reversed queue
    bool first = true;
    while (!q.empty()) {
        if (!first) cout << ' ';
        cout << q.front();
        q.pop();
        first = false;
    }
    cout << '\n';
    return 0;
}
