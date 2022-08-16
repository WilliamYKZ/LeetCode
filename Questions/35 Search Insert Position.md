# 35 Search Insert Position

Given a sorted array of distinct integers and a target value, return the index if the target is found. if not, return the index where it would be if it were inserted in order. 

You must write an algorithm with `O(log n)` runtime complexity. 



## C++ Binary Solution

```c++
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int numsSize = nums.size();

        int lowerKey = 0;
        int highestKey = numsSize - 1;
        while(lowerKey <= highestKey){
            int mid = lowerKey + (highestKey - lowerKey) / 2;
            if(nums[mid] < target){
                lowerKey = mid + 1;
            }else{
                highestKey = mid - 1;
            }
        }

        return lowerKey;
    }
};
```



## C++ Binar Solution But More Fast

```c++
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int lowerKey = 0;
        int highestKey = nums.size() - 1;
        int mid = 0;
        
        while(lowerKey <= highestKey){
            mid = (lowerKey + highestKey) / 2;
            if(nums[mid] == target){
                return mid;
            }else if(nums[mid] > target){
                highestKey = mid - 1;
            }else if(nums[mid] < target){
                lowerKey = mid + 1;
            }
        }
        if(lowerKey > mid){
            return lowerKey;
        }else{
            return mid;
        }
    }
};

```



