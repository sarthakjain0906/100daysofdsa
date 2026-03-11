/*Problem Statement:
Implement a Min Heap using an array where the smallest element is always at the root.

Supported Operations:
- insert x
- extractMin
- peek

Input Format:
- First line contains integer N
- Next N lines contain heap operations

Output Format:
- Print results of extractMin and peek
- Print -1 if operation cannot be performed

Example:
Input:
6
insert 40
insert 10
insert 30
peek
extractMin
peek

Output:
10
10
30*/
#include <bits/stdc++.h>
using namespace std;

struct MinHeap {
    vector<long long> a;

    inline int parent(int i) { return (i - 1) / 2; }
    inline int left(int i) { return 2 * i + 1; }
    inline int right(int i) { return 2 * i + 2; }

    void insert(long long x) {
        a.push_back(x);
        sift_up((int)a.size() - 1);
    }

    void sift_up(int i) {
        while (i > 0) {
            int p = parent(i);
            if (a[i] < a[p]) {
                swap(a[i], a[p]);
                i = p;
            } else break;
        }
    }

    long long* peek() {
        if (a.empty()) return nullptr;
        return &a[0];
    }

    long long* extractMin_val(long long &out) {
        if (a.empty()) return nullptr;
        out = a[0];
        a[0] = a.back();
        a.pop_back();
        if (!a.empty()) sift_down(0);
        return &out; // just to signal success
    }

    void sift_down(int i) {
        int n = (int)a.size();
        while (true) {
            int l = left(i), r = right(i), s = i;
            if (l < n && a[l] < a[s]) s = l;
            if (r < n && a[r] < a[s]) s = r;
            if (s == i) break;
            swap(a[i], a[s]);
            i = s;
        }
    }
};

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int N; 
    if (!(cin >> N)) return 0;
    MinHeap h;
    vector<string> out;

    for (int i = 0; i < N; ++i) {
        string cmd; 
        cin >> cmd;
        if (cmd == "insert") {
            long long x; cin >> x;
            h.insert(x);
        } else if (cmd == "peek") {
            auto p = h.peek();
            if (p) out.push_back(to_string(*p));
            else out.push_back("-1");
        } else if (cmd == "extractMin") {
            long long v;
            if (h.extractMin_val(v)) out.push_back(to_string(v));
            else out.push_back("-1");
        } else {
            out.push_back("-1"); // unknown command
        }
    }

    for (auto &s : out) cout << s << "\n";
    return 0;
}
