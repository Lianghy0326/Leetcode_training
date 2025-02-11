# 2/10
## 3174.Clear digits
### C++
``` c++
class Solution {
public:
    string clearDigits(string s) {
        string ans = "";
        stack<char> stk;
        for (char c : s){
            if (!isdigit(c)){
                stk.push(c);
            }
            else{
                stk.pop();
            }
        }
        while(!stk.empty()){
            ans = stk.top() + ans;
            stk.pop();
        }
        return ans;
    }
};
```

### Python
```python

```