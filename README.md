# Palindrome-Flipping

Chirag has a binary string S of length N. In one operation, Chirag can:
Select two indices i and j (1 ≤  i, j ≤ N, i ≠ j) and flip Si​ and Sj​. (i.e. change 0 to 1 and 1 to 0)
For example, if S = 10010 and chef applys operation on i = 1 and j = 3 then: 10010 → 00110.
Find if it is possible to convert S to a palindrome by applying the above operation any (possibly zero) number of times.
Note: A string is called a palindrome if it reads the same backwards and forwards, for e.g. 10001 and 0110 are palindromic strings.

#include <iostream>
#include <vector>
#include <string>
using namespace std;

void can_be_palindrome(int T, vector<pair<int, string>>& test_cases) {
    for (int t = 0; t < T; t++) {
        int N = test_cases[t].first;    
        string S = test_cases[t].second; 
        
        int mismatches = 0;
        for (int i = 0; i < N / 2; i++) {
            if (S[i] != S[N - i - 1]) {
                mismatches++;
            }
        }
        
        if (mismatches % 2 == 0 || N % 2 == 1) {
            cout << "Yes" << endl;
        } else {
            cout << "No" << endl;
        }
    }
}

int main() {
    int T;
    cin >> T;
    
    vector<pair<int, string>> test_cases(T);
    
    for (int i = 0; i < T; i++) {
        int N;
        string S;
        cin >> N >> S;
        test_cases[i] = {N, S};
    }
    
    can_be_palindrome(T, test_cases);
    
    return 0;
}
