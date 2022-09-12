# Exclusive or

1. is a logical operation that is true if and only if its arguments differ. 

![](https://github.com/WilliamYKZ/Picture/raw/main/Picture/Screen%20Shot%202022-09-12%20at%2016.18.12%20PM.png)

2. 可以理解为无进位的二进制加法。





## 用途

### 1.不用额外的变量交换两个数

```java
a = a ^ b;		// a = 甲 XOR 乙 b = 乙
b = a ^ b;		// a = 甲 XOR 乙 b = 甲 XOR 乙 XOR 乙 = 甲 XOR 0 = 甲
a = a ^ b;		// a = 甲 XOR 乙 XOR 甲 = 甲 XOR 甲 XOR 乙 = 乙
```

这个很好解释，在异或运算中， $0\  XOR\  N = N$, $N \ XOR \ X = 0$. 所以我们假设这个题目中 $a = 甲, b = 乙$。 



**注意：交换的两个数内存地址必须不一样，值可以一样，否则自己和自己异或等于0**



### 2.LeetCode 136 只出现一次的数字

题目：给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出只出现一次的元素。

例子：

```java
Input : [2,2,1]
Output: 1
```

代码：

```java
class Solution{
  public int singleNUmber(int[] nums){
    int temp = 0;
    int length = nums.length;
    for(int i = 0; i < length; i++){
      temp = temp ^ nums[i];
    }
    
    return temp;
  }
}
```





### 3. LeetCode 389 找不同

题目：给定两个字符串 `s` 和 `t` ，它们只包含小写字母。字符串 `t` 由字符串 `s` 随机重排，然后在随机位置添加一个字母。请找出在 `t` 中被添加的字母。

例子：

```java
Input: s = "abcd", t = "abcde"
Output: "e"
Explanation: 'e' is the letter that was added.
```

代码：

```java
class Solution {
    public char findTheDifference(String s, String t) {
        char res = 0;
        char[] chars = s.toCharArray();
        char[] chart = t.toCharArray();
        for (int i = 0; i < chars.length ; i++) {
            res ^= chars[i];
        }
        for (int i = 0; i < chart.length; i++) {
            res ^= chart[i];
        }
        return res;
    }
}
```



### 4. LeetCode 只出现一次的数字 II

题目：给你一个整数数组 nums，其中恰好有两个元素只出现一次，其余所有元素均出现两次。 找出只出现一次的那两个元素。你可以按 任意顺序 返回答案。

你必须设计并实现线性时间复杂度的算法且仅使用常量额外空间来解决此问题。

例子：

```java
Input: nums = [1,2,1,3,2,5]
Output: [3,5]
Explanation:  [5, 3] is also a valid answer.
```

代码：

```java
class Solution {
    public int[] singleNumber(int[] nums) {
        int temp = 0;
        for(int i = 0; i < nums.length; i++){
            temp ^= nums[i];
        }
        
        int rightOne = temp & (~temp + 1);
        int result1 = 0;
        
        for(int i = 0; i < nums.length; i++){
            if((nums[i] & rightOne) == 0){
                result1 ^= nums[i];
            }
        }
        
        return new int[]{result1, result1 ^ temp};
    }
}
```

