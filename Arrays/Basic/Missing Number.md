## Missing number in array [https://www.geeksforgeeks.org/problems/missing-number-in-array1416/1]

Given an array of size n-1 such that it only contains distinct integers in the range of 1 to n. Return the missing element.

## Examples:

Input: n = 5, arr[] = {1,2,3,5}

Output: 4

Explanation : All the numbers from 1 to 5 are present except 4.

Input: n = 2, arr[] = {1}

Output: 2

Explanation : All the numbers from 1 to 2 are present except 2.

Expected Time Complexity: O(n)

Expected Auxiliary Space: O(1)

Constraints:

1 ≤ n ≤ 106

1 ≤ arr[i] ≤ 106

## Logic Behind the Problem

- we have given n, and in the array there will n - 1 elements.
- so the sum of n natural numbers is `(n * (n + 1))/2`.
- for eg:- if n = 5 then sum of n numbers will `(5 * (5+1))/2 = 15`
- now in the array we have [1,2,3,5]. the sum of these numbers will be 11.
- Therefore, the subtraction of sum of n numbers and the sum of numbers in array i.e `15-11 = 4` will give us the missing number.

  # Code
  ```
  class Solution {

    // Note that the size of the array is n-1
    int missingNumber(int n, int arr[]) {

        // Your Code Here
        int totalsum = (n*(n+1))/2;
        int sum = 0;
        for(int i = 0; i < arr.length; i++){
            sum+=arr[i];
        }
        return totalsum - sum;
    }
  }
  ```
