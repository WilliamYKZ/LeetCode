# 121 Best Time to Buy and Sell Stock

You are given an array `price` where `price[i]` is the price of a given stock on the `ith` day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock. 

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return `0`. 

 

## C++ Solution

```C++
//最简单的方法就是直接枚举，但是这个方法时间复杂度是O（n^2）超时了
//所以现在我们要简化我们的循环结构
//读题之后我们可以发现，这个题最主要的就是最小值

class Solution {
public:
    int maxProfit(vector<int>& prices) {
        //首先我们要将prices的size写进int里面，然后进行对比排除不符合题目的prices 数组
        const int pricesSize = prices.size();
        if(pricesSize < 1){
            return 0;
        }
        
        vector<int> minPrices(pricesSize);
        vector<int> maxProfit(pricesSize);
        
        minPrices[0] = prices[0];
        maxProfit[0] = 0;
        
        for(int i = 1; i < pricesSize; i++){
            minPrices[i] = min(minPrices[i - 1], prices[i]);
            
            maxProfit[i] = max(maxProfit[i - 1], prices[i] - minPrices[i - 1]);
        }
        
        return maxProfit[pricesSize - 1];
    }
};

```



## Java Solution

```java
class Solution {
    public int maxProfit(int[] prices) {
        int pricesSize = prices.length;
        if(pricesSize < 1){
            return 0;
        }
        
        int[] minPrices = new int[pricesSize];
        int[] maxProfit = new int[pricesSize];
        
        minPrices[0] = prices[0];
        maxProfit[0] = 0;
        
        for(int i = 1; i < pricesSize; i++){
            minPrices[i] = Math.min(minPrices[i - 1], prices[i]);
            
            maxProfit[i] = Math.max(maxProfit[i - 1], prices[i] - minPrices[i - 1]);
        }
        
        return maxProfit[pricesSize - 1];
    }
}
```



## Python Solution

