**Merge Intervals** 

Leetcode - [https://leetcode.com/problems/merge-intervals/description/]

Youtube - [https://www.youtube.com/watch?v=zCLjBkLzK_s]

Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, 

and return an array of the non-overlapping intervals that cover all the intervals in the input.

Example 1:

Input: intervals = [[1,3],[2,6],[8,10],[15,18]]

Output: [[1,6],[8,10],[15,18]]

Explanation: Since intervals [1,3] and [2,6] overlap, merge them into [1,6].

Example 2:

Input: intervals = [[1,4],[4,5]]

Output: [[1,5]]

Explanation: Intervals [1,4] and [4,5] are considered overlapping.
 
Constraints:

1 <= intervals.length <= 104

intervals[i].length == 2

0 <= starti <= endi <= 104

**Explanation**

- To solve this problem, we first need to sort the intervals by their start times. In Java, we can use Arrays.sort with a custom comparator
  ```
  Arrays.sort(intervals, (arr1, arr2) -> arr1[0] - arr2[0]);
  ```
  Explanation of Arrays.sort with Custom Comparator:

- Arrays.sort is a built-in method in Java for sorting arrays.
- The second argument (arr1, arr2) -> arr1[0] - arr2[0] is a lambda expression defining the custom comparator.
- arr1 and arr2 are two sub-arrays being compared.
- arr1[0] - arr2[0] compares the first elements of these sub-arrays.
- If arr1[0] < arr2[0], the result is negative, meaning arr1 should come before arr2.
- If arr1[0] > arr2[0], the result is positive, meaning arr1 should come after arr2.
- If arr1[0] == arr2[0], the result is zero, meaning the order does not change.

Using a 2D Array List

- We use a List<int[]> to hold the merged intervals. Each element of this list is an array of integers (int[]), 
- which forms a 2D array-like structure when all elements are considered together.

```
List<int[]> output = new ArrayList<>();
```

**Complete Code**
```
class Solution {
    public int[][] merge(int[][] intervals) {
        Arrays.sort(intervals, (arr1, arr2) -> arr1[0] - arr2[0]);
        List<int[]> output = new ArrayList<>();
        int[] current = intervals[0];
        output.add(current);

        for (int[] interval : intervals) {
            int currentend = current[1];
            int nextbegin = interval[0];
            int nextend = interval[1];

            if (currentend >= nextbegin) {
                current[1] = Math.max(currentend, nextend);
            } else {
                current = interval;
                output.add(current);
            }
        }
        return output.toArray(new int[output.size()][]);
    }
}
```

**Iteration**
Given intervals = [[1, 3], [2, 6], [8, 10], [15, 18]]:

Initial State:

intervals after sorting: [[1, 3], [2, 6], [8, 10], [15, 18]]

output: []

current: [1, 3]

output after adding current: [[1, 3]]

First Iteration (interval = [1, 3]):

currentend = 3, nextbegin = 1, nextend = 3

currentend (3) >= nextbegin (1), so merge: current[1] = 3

output remains [[1, 3]]

Second Iteration (interval = [2, 6]):

currentend = 3, nextbegin = 2, nextend = 6

currentend (3) >= nextbegin (2), so merge: current[1] = 6

output updates to [[1, 6]]

Third Iteration (interval = [8, 10]):

currentend = 6, nextbegin = 8, nextend = 10

currentend (6) < nextbegin (8), so set new current: [8, 10]

output updates to [[1, 6], [8, 10]]

Fourth Iteration (interval = [15, 18]):

currentend = 10, nextbegin = 15, nextend = 18

currentend (10) < nextbegin (15), so set new current: [15, 18]

output updates to [[1, 6], [8, 10], [15, 18]]

Time Complexity: O(nlogn)

Space Complexity: O(n)

**Insert Intervals**

Leetcode - [https://leetcode.com/problems/insert-interval/]

Youtube - [https://www.youtube.com/watch?v=QPbbnxdLwSU]

You are given an array of non-overlapping intervals intervals where intervals[i] = [starti, endi] represent the start and the end of the ith interval and 

intervals is sorted in ascending order by starti. You are also given an interval newInterval = [start, end] that represents the start and end of another interval.

Insert newInterval into intervals such that intervals is still sorted in ascending order by starti and intervals still does not have any overlapping intervals 

(merge overlapping intervals if necessary).

Return intervals after the insertion.

Note that you don't need to modify intervals in-place. You can make a new array and return it.
 
Example 1:

Input: intervals = [[1,3],[6,9]], newInterval = [2,5]

Output: [[1,5],[6,9]]

Example 2:

Input: intervals = [[1,2],[3,5],[6,7],[8,10],[12,16]], newInterval = [4,8]

Output: [[1,2],[3,10],[12,16]]

Explanation: Because the new interval [4,8] overlaps with [3,5],[6,7],[8,10].
 
Constraints:

0 <= intervals.length <= 104

intervals[i].length == 2

0 <= starti <= endi <= 105

intervals is sorted by starti in ascending order.

newInterval.length == 2

0 <= start <= end <= 105

```
class Solution {
    public int[][] insert(int[][] intervals, int[] newInterval) {
        List <int[]> output = new ArrayList<>();
        int i = 0;
        
        while( i < intervals.length && intervals[i][1] < newInterval[0]){
            output.add(intervals[i]);
            i++;
        }

        while(i < intervals.length && intervals[i][0] <= newInterval[1]){
            newInterval[0] = Math.min(intervals[i][0], newInterval[0]);
            newInterval[1] = Math.max(intervals[i][1], newInterval[1]);
            i++;
        }

        output.add(newInterval);

        while(i < intervals.length){
            output.add(intervals[i]);
            i++;
        }

        return output.toArray(new int[output.size()][]);
    }
}
```
Time Complexity - O(n)

Space Complexity - O(n)
```
