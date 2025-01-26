Selection Sort is a simple sorting algorithm that repeatedly selects the smallest (or largest, depending on order) element from an unsorted portion of a list and places it at the beginning (or end) of the sorted portion.

## Example

1. Start with the first item in the list and assume it’s the smallest.
2. Go through the rest of the list to find the position of the smallest number.
3. After checking all the numbers, swap the smallest number with the one you’re currently looking at.
4. Move to the next position in the list and repeat the process for the remaining unsorted part.
5. Keep doing this until every number is in the correct position and the list is sorted.

Let’s consider an example with the following array of numbers:

```java
[17, 14, 9, 8, 7]
```

We start by assuming number `17` is the smallest.

```java
[->17<-, 14, 9, 8, 7]
```

Go through the rest of the list and find the smallest number.

```java
[17, ->14<-, 9, 8, 7] // 17 > 14 so we take 14 as the smallest
[17, 14, ->9<-, 8, 7] // 14 > 9 so we take 9 as the smallest
[17, 14, 9, ->8<-, 7] // 9 > 8 so we take 8 as the smallest
[17, 14, 9, 8, ->7<-] // 8 > 7 so we take 7 as the smallest
```

Set the smallest number as the first item in the array.

```java
[7 | 14, 9, 8, 17]
```

Now the first part of the array `[7]` is sorted, and the rest `[14, 9, 8, 17]` is unsorted.

Repeat the process for the remaining part until the entire array is sorted.

## Java Implementation

```java
public class Solution {
    public static void selectionSort(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n - 1; i++) {
            // Find the index of the smallest element in the unsorted part
            int minIndex = i;
            for (int j = i + 1; j < n; j++) {
                if (arr[j] < arr[minIndex]) {
                    minIndex = j; // Update the index of the smallest element
                }
            }

            // Swap the smallest element with the first element of the unsorted part
            int temp = arr[minIndex];
            arr[minIndex] = arr[i];
            arr[i] = temp;
        }
    }
}
```

## Time Complexity

- Best case: `O(n^2)`
- Average Case: `O(n^2)`
- Worst-case: `O(n^2)`

## Advantages

- Simple to understand and easy to implement.
- Does not require extra memory, as it sorts in place.
- Predictable performance with a fixed number of comparisons and swaps.
- Works well for small datasets.

## Disadvantages

- Inefficient for large datasets due to  O(n^2)  time complexity.
- Not a stable sort, so equal elements might not maintain their order.
- Performs unnecessary comparisons even if the array is already sorted.
- Involves frequent swaps, which adds overhead.

## Usage

- **Small datasets**: works well for small arrays where performance isn’t a concern.
- **Memory-constrained systems**: suitable for environments where additional memory allocation is not feasible.
- **Teaching tool**: often used to introduce sorting algorithms due to its simplicity.
- **Nearly unsorted data**: can handle completely unsorted data but is not efficient for partially sorted arrays.

---

**Parent:** [[_Sort]]