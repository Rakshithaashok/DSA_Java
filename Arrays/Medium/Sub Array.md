**Kadane's Algorithm**
Given an array Arr[] of N integers. Find the contiguous sub-array(containing at least one number) which has the maximum sum and return its sum.


Example 1:

Input:
N = 5
Arr[] = {1,2,3,-2,5}
Output:
9
Explanation:
Max subarray sum is 9
of elements (1, 2, 3, -2, 5) which 
is a contiguous subarray.
Example 2:

Input:
N = 4
Arr[] = {-1,-2,-3,-4}
Output:
-1
Explanation:
Max subarray sum is -1 
of element (-1)

Your Task:
You don't need to read input or print anything. The task is to complete the function maxSubarraySum() which takes Arr[] and N as input parameters and returns the sum of subarray with maximum sum.


Expected Time Complexity: O(N)
Expected Auxiliary Space: O(1)


Constraints:
1 ≤ N ≤ 106
-107 ≤ A[i] ≤ 107

**BruteForce Approach**
```
public class MaxSubArray {
    public static void main(String[] args) {
        int[] arr = {-2,-3,4,-1,-2,1,5,-3};
        int max = Integer.MIN_VALUE;
        for(int i = 0; i < arr.length; i++){
            for(int j = i; j < arr.length; j++) {
                int sum = 0;
                for (int k = i; k <= j; k++) {
                    sum += arr[k];
                }
                max = Math.max(sum, max);
            }
        }
        System.out.println(max);
    }
}
```
Time Complexity: 𝑂(𝑛^3)

Space Complexity: 𝑂(1)

**Better Solution**
```
public class MaxSubArray {
    public static void main(String[] args) {
        int[] arr = {-2,-3,4,-1,-2,1,5,-3};
        int max = Integer.MIN_VALUE;
        for(int i = 0; i < arr.length; i++){
            int sum = 0;
            for(int j = i; j < arr.length; j++) {
                sum += arr[j];
                max = Math.max(sum, max);
            }
        }
        System.out.println(max);
    }
}
```
Time Complexity: O(n^2)
Space Complexity: O(1)

**Optimized Solution** (Kadane's Algorithm)
```
class Solution{

    // arr: input array
    // n: size of array
    //Function to find the sum of contiguous subarray with maximum sum.
    long maxSubarraySum(int arr[], int n){
        
        // Your code here
        long sum = 0, max= Long.MIN_VALUE;
        for(int i = 0; i < arr.length; i++){
            sum+=arr[i];
            
            if(sum > max){
                max = sum;
            }
            
            if(sum < 0){
                sum = 0;
            }
        }
        return max;
    }
    
}
```
Time Complexity: 𝑂(𝑛)

Space Complexity: O(1)

**If asked to Print the sub-array**

