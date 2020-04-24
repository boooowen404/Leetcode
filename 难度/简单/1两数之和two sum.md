# 题目地址：
https://leetcode-cn.com/problems/two-sum/
## 我的代码：
#### 暴力解法：
```C++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> res;
        if(nums.size()<=1) return res;
        for(int i = 0; i<nums.size()-1; i++){
            for(int j = i+1; j<nums.size(); j++){
                if(nums[i]+nums[j]==target) {
                    res.push_back(i);
                    res.push_back(j);
                    return res;
                }
            }
        }
        return res;
    }
};
```
- 思路：最先想到的就是暴力搜索，遍历两遍数组，为了避免重复答案，可以从第一此遍历到的元素之后开始第二次遍历，也可以一定程度上优化时间复杂度
- 时间复杂度: o(N(N+1)/2)=o(N^2)
- 空间复杂度: o(1)

