# Dutch National Flag Algorithm for Three-Way Partitioning [https://www.geeksforgeeks.org/problems/three-way-partitioning/1]

## Problem Statement

Given an array of size `n` and a range `[a, b]`, the task is to partition the array around the range such that the array is divided into three parts:
1. All elements smaller than `a` come first.
2. All elements in the range `[a, b]` come next.
3. All elements greater than `b` appear at the end.

The individual elements of the three sets can appear in any order. You are required to return the modified array.

**Note:** The generated output is 1 if you modify the given array successfully.

**Geeky Challenge:** Solve this problem in O(n) time complexity.

### Example 1

**Input:** 
n = 5

array[] = {1, 2, 3, 3, 4}

[a, b] = [1, 2]

**Output:** 

**Explanation:** 
One possible arrangement is: `{1, 2, 3, 3, 4}`. If you return a valid arrangement, output will be 1.

### Example 2

**Input:** 

n = 6

array[] = {1, 4, 3, 6, 2, 1}

[a, b] = [1, 3]

**Output:** 

**Explanation:** 
One possible arrangement is: `{1, 3, 2, 1, 4, 6}`. If you return a valid arrangement, output will be 1.

## Task

You don't need to read input or print anything. The task is to complete the function `threeWayPartition()` which takes the array, `a`, and `b` as input parameters and modifies the array in place according to the given conditions.

**Expected Time Complexity:** O(n)  
**Expected Auxiliary Space:** O(1)

**Constraints:**
- 1 <= n <= 106
- 1 <= array[i], a, b <= 109

## Solution

To solve this problem, we use the Dutch National Flag Algorithm. This algorithm efficiently partitions the array into three parts with a time complexity of O(n) and a space complexity of O(1).

Here is the implementation in Java:

```java
class Solution {
    // Function to partition the array around the range such 
    // that the array is divided into three parts.
    public void threeWayPartition(int arr[], int a, int b) {
        int low = 0;
        int high = arr.length - 1;
        int mid = 0;
        int temp;
        
        while(mid <= high) {
            if(arr[mid] < a) {
                temp = arr[mid];
                arr[mid] = arr[low];
                arr[low] = temp;
                mid++;
                low++;
            } else if(arr[mid] > b) {
                temp = arr[mid];
                arr[mid] = arr[high];
                arr[high] = temp;
                high--;
            } else {
                mid++;
            }
        }
    }
}
```

## Explanation

### Initialization

- **low** and **mid** are initialized to the starting index (0).
- **high** is initialized to the ending index (`arr.length - 1`).

### Algorithm Steps

1. **Compare `arr[mid]` with `a`:**
   - If `arr[mid] < a`, swap `arr[mid]` with `arr[low]`. Increment both `low` and `mid` to move to the next elements.
   
2. **Compare `arr[mid]` with `b`:**
   - If `arr[mid] > b`, swap `arr[mid]` with `arr[high]`. Decrement `high`and don't increment `mid` because during swapping high element might have came front
   - so to check the swapped element `mid` should not increment.
   
3. **Within Range:**
   - If `arr[mid]` is within the range `[a, b]`, just increment `mid` to move to the next element.

### Loop Termination

- The loop continues until `mid` exceeds `high`.

### Key Points

- **Swapping** ensures that elements are rearranged without using extra space.
- **Incrementing/Decrementing Pointers:**
  - After swapping with **low**, both **low** and **mid** are incremented.
  - After swapping with **high**, only **high** is decremented. **Mid** is not incremented because the element swapped from the high end needs to be checked again.

### Example Walkthrough

Consider the array `arr = [1, 4, 3, 2, 5, 8]` with `a = 3` and `b = 5`:

1. Initial state: `low = 0`, `mid = 0`, `high = 5`.
2. `arr[mid] = 1` (less than `a`): Swap `arr[0]` and `arr[0]`. Increment both `low` and `mid`.
3. `arr[mid] = 4` (within range): Increment `mid`.
4. `arr[mid] = 3` (within range): Increment `mid`.
5. `arr[mid] = 2` (less than `a`): Swap `arr[2]` and `arr[1]`. Increment both `low` and `mid`.
6. `arr[mid] = 5` (within range): Increment `mid`.
7. `arr[mid] = 8` (greater than `b`): Swap `arr[5]` and `arr[5]`. Decrement `high`.

The final array is partitioned as `[1, 2, 3, 4, 5, 8]`.
