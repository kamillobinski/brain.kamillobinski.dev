Insertion Sort is a simple and intuitive sorting algorithm that works by dividing the array into a “sorted” and an “unsorted” portion. It iteratively takes one element from the unsorted portion and inserts it into its correct position in the sorted portion. This process is repeated until the entire array is sorted.

## Example

1. Start with the second element of the array (the first element is considered sorted).
2. Compare the current element with the elements in the sorted portion of the array (to its left).
3. Shift each element in the sorted portion one position to the right, until you find the correct position for the current element.
4. Insert the current element into its correct position in the sorted portion.
5. Move to the next element in the unsorted portion of the array and repeat steps 2–4.
6. Continue this process until all elements are in the sorted portion, and the entire array is sorted.

Let’s consider an example with the following array of numbers:

```java
[17, 14, 1, 20, 7]
```

Start with the first element `17`. Assume it is already sorted.

```java
[17 | 14, 1, 20, 7]
```

Take the second element `14`. Compare it with the sorted portion and insert it into the correct position.

```java
[14, 17 | 1, 20, 7]
```

Move to the third element `1`. Compare it with the sorted portion and insert it into the correct position.

```java
[1, 14, 17 | 20, 7]
```

Take the fourth element `1`. Compare it with the sorted portion and insert it into the correct position.

```java
[1, 14, 17, 20 | 7]
```

Finally, take the fifth element `7`. Compare it with the sorted portion and insert it into the correct position.

```java
[1, 7, 14, 17, 20]
```

## Java Implementation

```java
public class Solution {
    public static void insertionSort(int[] array) {
        for (int i = 1; i < array.length; i++) {
            int key = array[i];
            int j = i - 1;

            // Move elements of the sorted portion 
            // that are greater than the key one position
            // to the right
            while (j >= 0 && array[j] > key) {
                array[j + 1] = array[j];
                j--;
            }

            // Insert the key into its correct position
            array[j + 1] = key;
        }
    }
}
```

## Time Complexity

- Best case: `O(n)`
- Average case: `O(n^2)`
- Worst case: `O(n^2)`

## Advantages

- Easy to implement and understand.
- Performs well for small datasets.
- Faster on partially sorted arrays.
- Maintains the relative order of equal elements.
- Requires only a constant amount of extra memory.

## Disadvantages

- Slow for large datasets due to O(n^2) complexity.
- Lesss efficient compared to advanced sorting algorithms.
- Cannot utilize parallel processing effectively.
- Frequent shifting of elements increases overhead for large inputs.

## Usage

- **Small datasets**: ideal for sorting small arrays or lists due to its simplicity.
- **Partially sorted data**: efficient when the input is already partially sorted.
- **Real-time systems**: useful for systems requiring minimal overhead and predictable performance.
- **Learning purposes**: often used to teach sorting concepts due to its straightforward implementation.
- **Linked lists**: works well for sorting linked lists since shifting elements is not required.

---

**Parent**: [[_Sort]]