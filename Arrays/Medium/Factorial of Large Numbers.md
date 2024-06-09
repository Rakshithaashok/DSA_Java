[https://www.geeksforgeeks.org/problems/factorials-of-large-numbers2508/1]

**Factorials of large numbers**

Given an integer N, find its factorial. return a list of integers denoting the digits that make up the factorial of N.

Example 1:

Input: N = 5

Output: [1,2,0]

Explanation : 5! = 1*2*3*4*5 = 120

Example 2:

Input: N = 10

Output: [3,6,2,8,8,0,0]

Explanation :

10! = 1*2*3*4*5*6*7*8*9*10 = 3628800

Your Task:

You don't need to read input or print anything. Complete the function factorial() that takes integer

N as input parameter and returns a list of integers denoting the digits that make up the factorial of N.


Expected Time Complexity : O(N2)

Expected Auxilliary Space : O(1)

```
class Solution {
    static ArrayList<Integer> factorial(int N) {
        // code here
        ArrayList<Integer> output = new ArrayList<>();
        if(N == 0){
            output.add(0);
            return output;
        }
        if(N == 1){
            output.add(1);
            return output;
        }
        
        java.math.BigInteger result = java.math.BigInteger.ONE;
        for(int i = 2; i <= N; i++){
            result = result.multiply(java.math.BigInteger.valueOf(i));
        }
        
        String str = result.toString();
        for(int i = 0; i<str.length(); i++){
            output.add(Character.getNumericValue(str.charAt(i)));
            
        }
       
        return output;
    }
}
```
Constraints:
1 ≤ N ≤ 1000
