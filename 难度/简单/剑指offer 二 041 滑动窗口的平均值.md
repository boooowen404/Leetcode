# 题目地址：
https://leetcode.cn/problems/qIsx9U/
## 代码：
### 1.队列：
```C++
class MovingAverage {
public:
    /** Initialize your data structure here. */
    MovingAverage(int size) {
        winlen = size;
        winsum = 0;
    }
    
    double next(int val) {
        winsum+=val;
        temp.push(val);
        if(temp.size()<=winlen) return winsum/double(temp.size());
        winsum-=temp.front();
        temp.pop();
        return winsum/double(winlen);
    }
    int winsum;
    queue<int> temp;
    int winlen;//窗口长度
};
```
#### 思路：
队列的简单运用，注意类型转换，也可以直接把winsum定义为double
#### 复杂度分析：
- 时间复杂度: O(1)
- 空间复杂度: O(N)

