# Selection Sort

1. It has an [O](https://en.wikipedia.org/wiki/Big_O_notation)(*n*2) [time complexity](https://en.wikipedia.org/wiki/Time_complexity), which makes it inefficient on large lists, and generally performs worse than the similar [insertion sort](https://en.wikipedia.org/wiki/Insertion_sort). Selection sort is noted for its simplicity and has performance advantages over more complicated algorithms in certain situations, particularly where [auxiliary memory](https://en.wikipedia.org/wiki/Auxiliary_memory) is limited.
2. The algorithm divides the input list into two parts: a sorted sublist of items which is built up from left to right at the front (left) of the list and a sublist of the remaining unsorted items that occupy the rest of the list. Initially, the sorted sublist is empty and the unsorted sublist is the entire input list. The algorithm proceeds by finding the smallest (or largest, depending on sorting order) element in the unsorted sublist, exchanging (swapping) it with the leftmost unsorted element (putting it in sorted order), and moving the sublist boundaries one element to the right.



## 算法解释

1. `首先假设第一个值是最小值记为minIndex`，然后遍历数组，如果有更小的更新 `minIndex` 的值。 



## 代码

```java
public static void selectionSort(int[] arr){
  if(arr == null || arr.length < 2){
    return;
  }
  
  for(int i = 0; i < arr.length - 1; i++){
    int minIndex = i;
    for(int j = i + 1; j < arr.length; j++){
      minIndex = arr[j] < arr[minIndex] ? j : minIndex;
    }
    
    swap(arr, i , minIndex);
  }
}

public static void swap(int[] arr, int i, int j){
  int temp = arr[i];
  arr[i] = arr[j];
  arr[j] = temp;
}
```

