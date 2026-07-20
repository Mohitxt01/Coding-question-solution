# Coding-question-solution
Given a string containing just the characters '(' and ')', return the length of the longest valid (well-formed) parentheses substring. Example 1:Input: s = "(()"Output: 2Explanation: The longest valid parentheses substring is "()". Example 2:Input: s = ")()())"Output: 4Explanation: The longest valid parentheses substring is "()()".


#question
Given a string containing just the characters '(' and ')', return the length of the longest valid (well-formed) parentheses substring.
Example 1:Input: s = "(()"Output: 2Explanation: The longest valid parentheses substring is "()".
Example 2:Input: s = ")()())"Output: 4Explanation: The longest valid parentheses substring is "()()".
Example 3:Input: s = ""Output: 0
Constraints:
0 <= s.length <= 3 * 104
s[i] is '(', or ')'.

### Solution In C++

#include <iostream>
#include <stack>
#include <string>
#include <algorithm>
using namespace std;

int longestValidParentheses(string s) {
    stack<int> st;
    st.push(-1);  // Base index
    int maxLength = 0;

    for (int i = 0; i < s.length(); i++) {
        if (s[i] == '(') {
            st.push(i);
        } else {
            st.pop();

            if (st.empty()) {
                st.push(i);
            } else {
                maxLength = max(maxLength, i - st.top());
            }
        }
    }

    return maxLength;
}

int main() {
    string s;
    cin >> s;

    cout << longestValidParentheses(s) << endl;

    return 0;
}
