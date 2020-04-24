### 我的代码：
* 暴力解法：
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
时间复杂度：<a href="https://www.codecogs.com/eqnedit.php?latex=o\left&space;(&space;\frac{n\left&space;(&space;n&plus;1&space;\right&space;)}{2}&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?o\left&space;(&space;\frac{n\left&space;(&space;n&plus;1&space;\right&space;)}{2}&space;\right&space;)" title="o\left ( \frac{n\left ( n+1 \right )}{2} \right )" /></a>
