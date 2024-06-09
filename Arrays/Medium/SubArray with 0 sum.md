**Subarray with 0 sum**

GEEKSFORGEEKS:- [https://www.geeksforgeeks.org/problems/subarray-with-0-sum-1587115621/1]

Given an array of integers. Find if there is a subarray (of size at-least one) with 0 sum.

You just need to return true/false depending upon whether there is a subarray present with 0-sum or not. Printing will be taken care by the driver code.

Example 1:

Input:

n = 5

arr = {4,2,-3,1,6}

Output: 

Yes

Explanation: 

2, -3, 1 is the subarray with sum 0.

Example 2:

Input:

n = 5

arr = {4,2,0,1,6}

Output: 

Yes

Explanation: 

0 is one of the element in the array so there exist a subarray with sum 0.

Your Task:

You only need to complete the function subArrayExists() that takes array and n as parameters and returns true or false.

Expected Time Complexity: O(n).

Expected Auxiliary Space: O(n).

Constraints:

1 <= n <= 104

-105 <= a[i] <= 105

**Logic Building**

- Prefix Sum Technique:

One common approach to solve this problem is to use the prefix sum technique.

We create an array to store the prefix sum of elements encountered so far.

Iterate Through the Array:

As we iterate through the array, we keep track of the prefix sum.

If at any point, the prefix sum becomes 0 or if we encounter a prefix sum that we've seen before, it means there exists a subarray with a sum of 0.

- Using a HashSet:

To efficiently check if we've seen a prefix sum before, we can use a HashSet to store the prefix sums encountered so far.

If a prefix sum repeats, it means there's a subarray with a sum of 0.

- Algorithm Steps:

Initialize a HashSet to store prefix sums.

Initialize a prefix sum variable.

Iterate through the array.

At each iteration, add the current element to the prefix sum.

Check if the prefix sum is 0 or if it's already present in the HashSet.

If yes, return true.

If no, add the prefix sum to the HashSet.

If the loop completes without finding a subarray with a sum of 0, return false.

```
class Solution{
    //Function to check whether there is a subarray present with 0-sum or not.
    static boolean findsum(int arr[],int n)
    {
        //Your code here
        HashMap<Integer, Boolean> map = new HashMap<>();
        int sum = 0;;
        for(int i = 0;  i < n; i++){
            sum+=arr[i];
            if(sum==0 || map.containsKey(sum))
                return true;
            map.put(sum, true);
        }
        return false;
    }
}
```

Time Complexity : O(n)

Space Complexity : O(n)
