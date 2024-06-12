## Find minimum and maximum element in an array [https://www.geeksforgeeks.org/problems/find-minimum-and-maximum-element-in-an-array4428/1]

Given an array A of size N of integers. Your task is to find the minimum and maximum elements in the array.

Note: Return an array that contains 2 elements the first one will be a minimum element and the second will be a maximum of an array.

## Example 1:

Input:

N = 6

A[] = {3, 2, 1, 56, 10000, 167}

Output: 1 10000

Explanation: minimum and maximum elements of array are 1 and 10000.
 
## Example 2:

Input:

N = 5

A[]  = {1, 345, 234, 21, 56789}

Output: 1 56789

Explanation: minimum and maximum element of array are 1 and 56789.
 
## Your Task:  

You don't need to read input or print anything. Your task is to complete the function getMinMax() which takes the array A[] and its size N as inputs and returns the minimum and maximum element of the array.

Expected Time Complexity: O(N)

Expected Auxiliary Space: O(1)

Constraints:

1 <= N <= 105

1 <= Ai <=1012

## Code

```
//User function Template for Java

/*
 class Pair  
{  
    long first, second;  
    public Pair(long first, long second)  
    {  
        this.first = first;  
        this.second = second;  
    }  
} 

Java users need to return result in Pair class
For Example -> return new Pair(minimum,maximum)
*/

class Solution 
{
    static Pair getMinMax(long arr[], long n)  
    {
        //Write your code here
        long min = Integer.MAX_VALUE;
        long max = Integer.MIN_VALUE;
        for(int i = 0; i < n; i++){
            if(arr[i] < min)
                min = arr[i];
            if(arr[i] > max)
                max = arr[i];
        }
        return new Pair(min, max);
    }
}

```
#
