# Chocolate Distribution Problem [https://www.geeksforgeeks.org/problems/chocolate-distribution-problem3825/1]

## Problem Statement

Given an array `A[]` of positive integers of size `N`, where each value represents the number of chocolates in a packet, and there are `M` students, the task is to distribute chocolate packets among `M` students such that:
1. Each student gets exactly one packet.
2. The difference between the maximum number of chocolates given to a student and the minimum number of chocolates given to a student is minimized.

## Example

### Input:
- N = 8
- M = 5
- A = {3, 4, 1, 9, 56, 7, 9, 12}

### Output:
6

Explanation: The minimum difference between the maximum chocolates and minimum chocolates is 9 - 3 = 6 by choosing the following `M` packets: {3, 4, 9, 7, 9}.

## Approach

1. **Sort the array**: Sort the array of chocolate packets in ascending order.
    - **Explanation**: Sorting ensures that packets with similar numbers of chocolates are placed closer to each other, facilitating fair distribution.
2. **Use a sliding window**: Initialize two pointers `start` and `end`. Set `start = 0` and `end = start + (M - 1)`.
    - **Explanation**: Sliding window technique helps in traversing the sorted array efficiently.
3. **Iterate through the array**: While `end` is less than the size of the array:
   - Calculate the difference between the elements at `end` and `start`.
   - Update the minimum difference found so far.
   - Move both pointers (`start` and `end`) to the right by one position.
4. **Return the minimum difference**.

## Time Complexity
- Sorting the array: O(N*log(N))
- Sliding window traversal: O(N)
- Overall: O(N*log(N))

## Space Complexity
- Sorting the array in-place: O(1)

## Implementation

```java
import java.util.ArrayList;
import java.util.Collections;

class Solution {
    public long findMinDiff(ArrayList<Integer> a, int n, int m) {
        Collections.sort(a); // Doubt: Why are we sorting initially?
        long min = Integer.MAX_VALUE;
        int start = 0;
        int end = start + (m - 1);
        while (end < n) {
            min = Math.min(min, a.get(end) - a.get(start)); // Doubt: How does sliding window help in finding the minimum difference?
            end++;
            start++;
        }
        return min;
    }
}
```
