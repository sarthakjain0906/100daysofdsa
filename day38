/*Problem: Deque (Double-Ended Queue)

A Deque is a linear data structure that allows insertion and deletion of elements from both the front and the rear. It provides more flexibility than a standard queue or stack.

Common Operations:
1. push_front(value): Insert an element at the front of the deque.
2. push_back(value): Insert an element at the rear of the deque.
3. pop_front(): Remove an element from the front of the deque.
4. pop_back(): Remove an element from the rear of the deque.
5. front(): Return the front element of the deque.
6. back(): Return the rear element of the deque.
7. empty(): Check whether the deque is empty.
8. size(): Return the number of elements in the deque.

Additional Operations:
- clear(): Remove all elements from the deque.
- erase(): Remove one or more elements from the deque.
- swap(): Swap contents of two deques.
- emplace_front(): Insert an element at the front without copying.
- emplace_back(): Insert an element at the rear without copying.
- resize(): Change the size of the deque.
- assign(): Replace elements with new values.
- reverse(): Reverse the order of elements.
- sort(): Sort the elements in ascending order.

Time Complexity:
- push_front, push_back, pop_front, pop_back, front, back, empty, size: O(1)
- clear, erase, resize, assign, reverse: O(n)
- sort: O(n log n)

Input:
- Sequence of deque operations with values (if applicable)

Output:
- Results of operations such as front, back, size, or the final state of the deque after all operations*/
#include <bits/stdc++.h>
using namespace std;

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    
    int q; 
    if (!(cin >> q)) return 0;
    deque<long long> dq;
    vector<string> out;

    for (int _ = 0; _ < q; ++_) {
        string cmd; 
        cin >> cmd;

        if (cmd == "push_front") {
            long long x; cin >> x; dq.push_front(x);
        } else if (cmd == "push_back") {
            long long x; cin >> x; dq.push_back(x);
        } else if (cmd == "pop_front") {
            if (!dq.empty()) { out.push_back(to_string(dq.front())); dq.pop_front(); }
            else out.push_back("error");
        } else if (cmd == "pop_back") {
            if (!dq.empty()) { out.push_back(to_string(dq.back())); dq.pop_back(); }
            else out.push_back("error");
        } else if (cmd == "front") {
            out.push_back(dq.empty() ? "error" : to_string(dq.front()));
        } else if (cmd == "back") {
            out.push_back(dq.empty() ? "error" : to_string(dq.back()));
        } else if (cmd == "empty") {
            out.push_back(dq.empty() ? "1" : "0");
        } else if (cmd == "size") {
            out.push_back(to_string((int)dq.size()));
        } else if (cmd == "clear") {
            dq.clear();
        } else if (cmd == "reverse") {
            reverse(dq.begin(), dq.end());
        } else if (cmd == "sort") {
            sort(dq.begin(), dq.end());
        } else if (cmd == "assign") {
            int k; long long val; cin >> k >> val;
            dq.assign(k, val);
        } else if (cmd == "resize") {
            int n; long long val = 0;
            string maybe; 
            cin >> n;
            if (cin.peek() == ' ') { 
                if (cin >> val) { /* ok */ } 
            }
            dq.resize(n, val);
        } else if (cmd == "erase") {
            // erase idx OR erase l r (inclusive)
            string a; cin >> a;
            if (cin.peek() == '\n' || cin.peek() == '\r') {
                int idx = stoi(a);
                if (0 <= idx && idx < (int)dq.size()) dq.erase(dq.begin() + idx);
                else out.push_back("error");
            } else {
                int l = stoi(a), r; cin >> r;
                if (0 <= l && l <= r && r < (int)dq.size())
                    dq.erase(dq.begin() + l, dq.begin() + r + 1);
                else out.push_back("error");
            }
        } else {
            out.push_back("error");
        }
    }

    for (auto &s : out) cout << s << "\n";
    return 0;
}
