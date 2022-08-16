# 349 Intersection of Two Array

Given two integer array `nums1` and `nums2`, return an array of their intersection. Each element in the result must be unique and you may return the result in any order.

Example:

```
Input : nums1 = [1,2,2,1], nums2 = [2,2]
OutPut : [2]
```

```
Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [9,4]
```





## HashSet

```c++
class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {
        unordered_set<int> set1;
        unordered_set<int> set2;
        
        for(auto& num : nums1){
            set1.insert(num);
        }
        
        for(auto& num : nums2){
            set2.insert(num);
        }
        
        return findIntersection(set1, set2);
    }
    
    vector<int> findIntersection(unordered_set<int>& set1, unordered_set<int>& set2){
        if(set1.size() > set2.size()){
            return findIntersection(set2,set1);
        }
        
        vector<int> intersection;
        for(auto& num : set1){
            if(set2.count(num) != 0){
                intersection.push_back(num);
            }
        }
        
        return intersection;
    }
};
```

