# [移掉K位数字](https://leetcode-cn.com/problems/remove-k-digits/)
```cpp
class Solution {
public:
    string removeKdigits(string num, int k) {
        stack<char> myStack;
        for(auto c:num){
            while (!myStack.empty()&&k>0&&myStack.top()>c){
                myStack.pop();
                k--;
            }
            if(myStack.empty()&&c=='0') continue;
            myStack.push(c);
        }
        string ans;
        while (!myStack.empty()){
            if(k>0) k--;
            else ans+=myStack.top();
            myStack.pop();
        }
        reverse(ans.begin(),ans.end());
        return ans==""?"0":ans;
    }
};
```