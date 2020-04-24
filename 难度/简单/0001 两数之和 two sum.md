# 题目地址：
https://leetcode-cn.com/problems/two-sum/
## 代码：
### 1.暴力解法：
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
#### 思路：
最先想到的就是暴力搜索，遍历两遍数组，为了避免重复答案，可以从第一此遍历到的元素之后开始第二次遍历，也可以一定程度上优化时间复杂度
#### 复杂度分析：
- 时间复杂度: O(N(N+1)/2)=O(N^2)
- 空间复杂度: O(1)
#### 优化：
```C++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int len=nums.size();
        for(int i=0;i<len-1;i++) for(int j=i+1;j<len;j++)
        {
            if(nums[i]+nums[j] == target)
            return {i,j};
        }
       return {};
    }
};
```
### 2.哈希表：
```C++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> m;
        for(int i=0; i<nums.size();i++)
        {
            if(m.find(target-nums[i])!=m.end()) 
                return {m[target-nums[i]], i};
            m[nums[i]]=i;
        }
        return {};
    }
};
```
#### 思路：
用哈希表记录数组中每个元素的下标，在遍历时直接看是否存在target-nums[i]即可，遍历一次
一般的想法是先构建哈希表，再遍历第二遍查找差值，但是实际上可以一次完成
对于可能出现的重复元素，哈希表中记录的是第二个位置，所以不影响结果的正确性
对于target-nums[i]=nums[i]的情况，由于哈希表中还没有记录，所以不用特殊处理
#### 复杂度分析：
- 时间复杂度: O(N)
- 空间复杂度: O(N)


## 总结：
1、unordered_map 核心特点：无序存储+常数时间内的查找
2、unorder_map的查找操作比map更快，但占用内存略高；map基于红黑树，unordered_map基于vector
3、vector的初始化方式决定了可以直接返回{}
4、边界条件有时可以直接包含到后续的处理中
