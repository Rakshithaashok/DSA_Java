# Count the Number of Digits in N Which Evenly Divide N [https://www.geeksforgeeks.org/problems/count-digits5716/1]

Given a number N, the task is to count the number of digits in N which evenly divide N.

**Note**: Evenly divides means that N is divisible by a digit (i.e., leaves a remainder of 0 when divided).

## Examples

### Example 1

Input:

N = 12

Output:

2

Explanation:

1 and 2 both divide 12 evenly.

### Example 2

Input:

N = 23

Output:

0

Explanation:

Neither 2 nor 3 divides 23 evenly


## Your Task
You don't need to read input or print anything. Your task is to complete the function `evenlyDivides()` which takes an integer `N` as input parameters and returns an integer, the total number of digits of `N` which divide `N` evenly.

## Expected Complexity
- **Time Complexity**: O(log N)
- **Space Complexity**: O(1)

## Constraints
- 1<=N<=105

## Solution

```java
class Solution {
    static int evenlyDivides(int N) {
        int count = 0;
        int temp = N; 
        while (N != 0) {
            int digit = N % 10; 
            if (digit != 0 && temp % digit == 0)
                count++;
            N = N / 10;
        }
        return count;
    }
}
```

Explanation

Variables:

- count: To keep track of the number of digits that evenly divide N.
- temp: To store the original value of N for the modulus operation.

Algorithm:

- Loop through each digit of N by repeatedly taking N % 10 and then dividing N by 10.
- For each digit, check if the digit is not zero and if it evenly divides temp.
- If both conditions are satisfied, increment the count.
- Finally, return the count after processing all digits.
