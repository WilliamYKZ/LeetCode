# 217 Contains Duplicate

Given an integer array `nums`, return `true` if any value appears at least twice in the array, and return `false` if every element is distinct. 



## C++ Order Solution

```C++
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        int numsSize = nums.size();
        sort(nums.begin(), nums.end());
        
        for(int i = 0; i < numsSize - 1; i++){
            if(nums[i] == nums[i+1]){
                return true;
            }
        }
        
        return false;
    }
};
```



## C++ Hash Solution

```c++
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
      unordered_set<int> s;
      for(int i : nums){
        if(s.find(i) != s.end()){
          return true;
        }s.insert(i);
      }
      return false;
    }
};
```

