**Common Elements**

Given three arrays sorted in increasing order. Find the elements that are common in all three arrays.

Note: can you take care of the duplicates without using any additional Data Structure?

Example 1:

Input:

n1 = 6; A = {1, 5, 10, 20, 40, 80}

n2 = 5; B = {6, 7, 20, 80, 100}

n3 = 8; C = {3, 4, 15, 20, 30, 70, 80, 120}

Output: 20 80

Explanation: 20 and 80 are the only

common elements in A, B and C.
 
Your Task:  

You don't need to read input or print anything. Your task is to complete the function commonElements() which take the 3 arrays A[], B[], C[] and their respective sizes n1, n2 and n3 as inputs and returns an array containing the common element present in all the 3 arrays in sorted order. 

If there are no such elements return an empty array. In this case the output will be printed as -1.

Expected Time Complexity: O(n1 + n2 + n3)

Expected Auxiliary Space: O(n1 + n2 + n3)

Constraints:

1 <= n1, n2, n3 <= 10^5

The array elements can be both positive or negative integers.

```
class Solution
{
    ArrayList<Integer> commonElements(int A[], int B[], int C[], int n1, int n2, int n3) 
    {
        // code here 
        
        HashSet <Integer> output = new HashSet<Integer>();
        HashSet <Integer> output2 = new HashSet<Integer>();
        ArrayList <Integer> output3 = new ArrayList<Integer>();

        for(int i = 0; i < n1; i++){
            output.add(A[i]);
        }
        
        for(int j = 0; j < n2; j++){
            if(output.contains(B[j])){
                output2.add(B[j]);
            }
        }
        
        for(int k = 0; k < n3; k++){
            if((output2.contains(C[k])) && (!output3.contains(C[k]))){
                output3.add(C[k]);
            }
        }
        return output3;
    }
}
```
