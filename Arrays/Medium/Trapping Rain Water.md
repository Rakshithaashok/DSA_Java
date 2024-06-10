Geeks for Geeks - [https://www.geeksforgeeks.org/problems/trapping-rain-water-1587115621/1]

Leetcode - [https://leetcode.com/problems/trapping-rain-water/description/]

```
class Solution{
    
    // arr: input array
    // n: size of array
    // Function to find the trapped water between the blocks.
    static long trappingWater(int arr[], int n) { 
        // Your code here
        long result = 0;
        long leftmax = 0;
        long rightmax = 0;
        int left = 0;
        int right = n-1;
        while(left <= right){
            if(arr[left] <= arr[right]){
                if(arr[left] >= leftmax){
                    leftmax = arr[left];
                }
                else{
                    result += leftmax - arr[left];
                }
                left++;
            }
            else{
                if(arr[right] >= rightmax){
                    rightmax = arr[right];
                }
                else{
                    result+=rightmax - arr[right];
                }
                right--;
            }
        }
        return result;
    } 
}
```

Time Complexity - O(n)

Space Complexity - O(1)
