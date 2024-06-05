**Cyclically rotate an array by one** [https://www.geeksforgeeks.org/problems/cyclically-rotate-an-array-by-one2614/1]
Given an array, rotate the array by one position in clock-wise direction.
 

Example 1:

Input:
N = 5
A[] = {1, 2, 3, 4, 5}
Output:
5 1 2 3 4
 

Example 2:

Input:
N = 8
A[] = {9, 8, 7, 6, 4, 2, 1, 3}
Output:
3 9 8 7 6 4 2 1
 

Your Task:  
You don't need to read input or print anything. Your task is to complete the function rotate() which takes the array A[] and its size N as inputs and modify the array in place.

 

Expected Time Complexity: O(N)
Expected Auxiliary Space: O(1)

 

Constraints:
1<=N<=105
0<=a[i]<=105

```
class Compute {
    
    public void rotate(int arr[], int n)
    {
        int temp = arr[n - 1];
        int j = arr.length - 2;
        while(j >= 0){
            arr[j+1] = arr[j];
            j--;
        }
        arr[0] = temp;
        
    }
}
```
Time Complexity: O(n), where n is the length of the array.

Space Complexity: O(1), since only a constant amount of extra space is used regardless of the input size.
