# 238 Product of Array Except Self

Given an integer array `nums`, return an array `answer` such that `answer[i]` is equal to the product of all elements of `nums` except `nums[i]` 

The product of any prefix or suffic of `nums` is guaranteed to fit in a 32-bit integer. 

You must write an algorithm that runs in `O(n)` time and without using the division operation. 



## 左右乘积表

这个题目之需要将锁定数字的左边所有数和右边所有数乘起来就可以了。也就是前缀乘后缀。

1. 那么我们首先建立一个记录左边数的数组，其中数组的第一位应该是1，应为左边数组左边没有元素。而1乘其他数还是原来的数。开始循环，我们需要用第一个nums中的数字乘第一个L中的数字，得到L中第二个数字。
2. R同理，然后我们将L乘R就可以得到Answer



![](/Users/williamyan/Documents/1_LearningDocument/CS/3_Algorithm/Picture/JPEG image-111C7EEC9ED5-1.jpeg)



**时间复杂度为 O(n)**: 因为我们没有用for套用for，用了三个for循环，时间复杂度都为O(n)

**空间复杂度 O(n)**: 输出数组不算进空间复杂度中，因此我们之需要常数的空间存放变量。

### C++ 实现

```c++
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int numsSize = nums.size();
        
        vector<int> leftHandSide(numsSize, 0);
        vector<int> rightHandSide(numsSize, 0);
        vector<int> answer(numsSize);
        
        leftHandSide[0] = 1;
        for(int i = 1; i < numsSize; i++){
            leftHandSide[i] = nums[i - 1] * leftHandSide[i - 1];
        }
        
        rightHandSide[numsSize -1] = 1;
        for(int i = numsSize -2; i >= 0; i--){
            rightHandSide[i] = nums[i + 1] * rightHandSide[i + 1];
        }
        
        for(int i = 0; i < numsSize; i++){
            answer[i] = leftHandSide[i] * rightHandSide[i];
        }
        
        return answer;
    }
};
```





## 减少空间复杂度

```c++
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int numsSize = nums.size();
        
        vector<int> answer(numsSize);
        
        answer[0] = 1;
        for(int i = 1; i < numsSize; i++){
            answer[i] = nums[i - 1] * answer[i - 1];
        }
        
        int R = 1;
        for(int i = numsSize - 1; i >= 0; i--){
            answer[i] = answer[i] * R;
            R = R * nums[i];
        }
        return answer;
    }
};
```



## Questions

1. 建立vector的时候 `vector<int> L(length, 0);` 0是什么东西