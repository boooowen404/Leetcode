# 题目地址：
https://leetcode-cn.com/problems/valid-parentheses/
## 代码：
### 1.栈：
```C++
class Solution {
public:
    bool isValid(string s) {
        stack<int> sta;
        for(auto i:s)
        {
            if(i == '('||i == '['||i == '{') sta.push(i);
            else
            {
                if(sta.empty()) return false;
                if(i==')'&&sta.top()!='(') return false;
                if(i==']'&&sta.top()!='[') return false;
                if(i=='}'&&sta.top()!='{') return false;
                sta.pop();
            }
        }
        return sta.empty();
    }
};
```
#### 思路：
利用栈，将左括号放到栈里，遇到右括号就从栈里取出一个匹配，直到匹配时发现栈空或匹配错误，匹配完字符串后如果栈非空，证明有多余的左括号
#### 复杂度分析：
- 时间复杂度: O(N)
- 空间复杂度: O(N)

## 总结：
1、stack为空时使用top()会报错
2、注意两种情况，第一有多余的左括号，此时匹配完成后栈非空，第二有多余的右括号，此时匹配时栈为空
