# 53 Maximum Subarray

Given an integer array `nums`, find the contiguous subarray(containing at least one number) which has the largest sum and return its sum. 

A subarray is a contiguous part of an array. 



## 方法1：动态规划（贪心算法）

也就是我们先锁定第一个数组中的数，设置两个变量，一个记录i之前的所有的数字相加之和，另一个记录最大的和。那么如果i之前所有的数字相加，我们就抛弃i之前的所有数字，从i之后的数字开始算。

### C++ 实现

```c++
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int beforeNumberSum = 0;
        int maxSum = nums[0];
        
        for(int i = 0; i < nums.size(); i++){
            if(beforeNumberSum < 0){
                beforeNumberSum = 0;
            }
            
            beforeNumberSum = beforeNumberSum + nums[i];
            maxSum = max(maxSum, beforeNumberSum);
        }
        
        return maxSum;
    }
};

//同样的动态规划，更加严谨
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int beforeNumber = 0;
        int maxSum = nums[0];
        
        for(const auto &x : nums){
            beforeNumber = max(beforeNumber + x, x);
            maxSum = max(maxSum, beforeNumber);
        }
        
        return maxSum;
    }
};
```

**时间复杂度** O(n)：其中n为`nums` 数组长度，我们只需要遍历一遍数组就可以了。

**空间复杂度** O(n):  我们只需要常数空间存放若干变量。