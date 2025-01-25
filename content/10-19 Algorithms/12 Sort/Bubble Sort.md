Bubble Sort is a sorting algorithm based on comparisons. It repeatedly compares each pair of adjacent elements and swaps them if they are not in the correct order. This process continues until the list is fully sorted.

The name “Bubble Sort” comes from the way smaller or larger elements “bubble” to the top of the list. Since the algorithm relies solely on comparisons to manipulate elements, it is classified as a comparison-based sorting method. While the algorithm is simple, it is generally too slow and inefficient for most practical applications, especially when compared to more advanced sorting algorithms like Insertion Sort. However, it can be useful in scenarios where the input data is mostly sorted but may contain a few misplaced elements.

## Example

1. Start with the first element of the array.
2. Compare the current element with the next element:
   - if the current element is greater than the next, swap them,
   - if the current element is smaller, leave them as they are.
3. Move to the next pair of elements and repeat the comparison and swapping process.
4. Continue this process for each element in the array until the largest element “bubbles” to the end.
5. Repeat the entire process for the remaining unsorted part of the array until the entire array is sorted.

Let’s consider an example with the following array of numbers:

```java
[17, 14, 9, 8, 7]
```

We start by comparing the first two elements in the array. If the first element is greater than the second, we swap them. Otherwise, we leave them unchanged. In this case, `17` is greater than `14`, so we swap them:

```java
[(17, 14), 9, 8, 7] -> [14, 17, 9, 8, 7]
```

Next, we compare the second and third elements in the array. If the second element is greater than the third, we swap them. Otherwise, we leave them unchanged. In this case, `17` is greater than `9`, so we swap them:

```java
[14, (17, 9), 8, 7] -> [14, 9, (17, 8), 7] -> [14, 9, 8, (17, 7)] -> [14, 9, 8, 7, 17]
```

We have now completed one pass through the array. We repeat this process until the array is sorted. In this case, we need to repeat the process three more times:

```java
Pass 2: [9, 8, 7, 14, 17]
Pass 3: [8, 7, 9, 14, 17]
Pass 4: [7, 8, 9, 14, 17]
```

## Java Implementation

```java
public class Solution {
    public static void bubbleSort(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n - 1; i++) {
            for (int j = 0; j < n - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
    }
}
```

> [!info] Optimized

```java
public class Solution {
    public static void optimizedBubbleSort(int[] arr) {
        int n = arr.length;
        boolean swapped;
        for (int i = 0; i < n - 1; i++) {
            swapped = false;
            for (int j = 0; j < n - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                    swapped = true;
                }
            }
            if (!swapped) break;
       }
    }
}
```

### Complexity

- Best case: `O(n)`
- Average case: `O(n^2)`
- Worst case: `O(n^2)`

## Advantages

- Simple to understand and implement.
- Requires no additional memory as it sorts the array in place.
- Works well for small datasets where performance is not critical.
- Optimized versions can detect if the array is already sorted and terminate early.

## Disadvantages

- Highly inefficient for large datasets due to its O(n^2) time complexity.
- Much slower compared to other sorting algorithms like Quick Sort or Merge Sort.
- Performance decreases significantly as the dataset size increases.
- Involves a high number of swaps, which adds unnecessary overhead for larger arrays.

## Usage

- **Small datasets**: simple and effective for small arrays.
- **Nearly sorted data**: efficient with optimized early exit.
- **Embedded systems**: works in memory-constrained environments.
- **Teaching tool**: ideal for learning sorting concepts.

---

**Parent**: [[_Sort]]