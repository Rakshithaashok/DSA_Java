## Third largest element [https://www.geeksforgeeks.org/problems/third-largest-element/1]

Given an array of distinct elements. Find the third largest element in it.

Suppose you have A[] = {1, 2, 3, 4, 5, 6, 7}, its output will be 5 because it is the 3 largest element in the array A.

## Example 1:

Input:

N = 5

A[] = {2,4,1,3,5}

Output: 3

## Example 2:

Input:

N = 2

A[] = {10,2}

Output: -1

## Your Task:

Complete the function thirdLargest() which takes the array a[] and the size of the array, n, as input parameters and returns the third largest element in the array. It return -1 if there are less than 3 elements in the given array.

Expected Time Complexity: O(N)

Expected Auxiliary Space: O(1)

Constraints:

1 ≤ N ≤ 105

1 ≤ A[i] ≤ 105

## Code 
```
class Solution
{
    int thirdLargest(int arr[], int n)
    {
	    // Your code here
	    if(n < 4)
	        return -1;
	    int firstmax = Integer.MIN_VALUE;
	    int secondmax = Integer.MIN_VALUE;
	    int thirdmax = Integer.MIN_VALUE;
	    for(int i = 0; i < n; i++){
	        if(arr[i] > firstmax){
	            thirdmax = secondmax;
	            secondmax = firstmax;
	            firstmax = arr[i];
	        }
	        else if(arr[i] > secondmax){
	            thirdmax = secondmax;
	            secondmax = arr[i];
	        }
	        else if(arr[i] > thirdmax){
	            thirdmax = arr[i];
	        }
	    }
	    return thirdmax;
    }
}
```
