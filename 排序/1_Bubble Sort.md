# Bubble Sort

1. A simple sorting algorithm that repeatedly steps through the input list element by element comparing the current element with the one after it, swapping their value if needed. These passes through the list are repeated until no swaps had to be performed during a pass, meaning that the list has become fully sorted.
2. Bubble sort has a worst-case and average complexity of $O(n^2)$, where $n$ is the number of items being sorted. Even other $O(n^2)$ sorting algorithms, such as insertion sort, generally run faster than bubble sort. 
3. 空间复杂度为 $O(1)$: 只需要原地交换，使用常熟大小的额外空间。



## 算法解析

- 内循环：使用相邻双指针 `j`， `j+1`从左到右遍历，一次比较相邻元素的大小，如果左元素大于右元素则将他们交换；遍历完成时，最大的元素会被交换到数组最右边。
- 外循环：不断重复内存换，每轮将当前最大元素交换到剩余未排序数组最右边，直到所有元素都被交换到正确位置时结束。



## 代码

```java
void bubbleSort(int[] nums){
  int numsLength = nums.length;
  
  for(int i = 0; i < numsLength - 1; i++){
    for(int j = 0; j < numsLength - i - 1; j++){
      
      if(nums[j] > nums[j+1]){
        swap(nums, nums[j],nums[j+1])
      }
    }
  }
}

void swap(int[] nums, nums[j], nums[j+1]]){
  int temp = nums[j];
	nums[j] = nums[j + 1];
  nums[j + 1] = tmp;
}
```



