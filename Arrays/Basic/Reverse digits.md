# Reverse Digits of a Given Number

Given an integer \( N \), the task is to reverse the digits of the given number \( N \), ensuring that the reversed number has no leading zeroes. Return the resulting reversed number.

## Examples

### Example 1

Input: 200

Output: 2

Explanation: By reversing the digits of the number, the number will change into 2.

### Example 2

Input: 122

Output: 221

Explanation: By reversing the digits of the number, the number will change into 221.

## Your Task
You don't need to read or print anything. Your task is to complete the function `reverse_digit()` which takes \( N \) as an input parameter and returns the reversed number.

## Expected Complexity
- **Time Complexity**: O(Log(N))
- **Space Complexity**: O(1)

```
class Solution {
    public long reverse_digit(long n) {
        // Code here
        long digit = 0;
        while (n != 0) {
            long mod = n % 10;
            digit = digit * 10 + mod;
            n = n / 10;
        }
        return digit;
    }
}
```

### Explanation of Key Step
- digit = digit * 10 + mod:
- Initially, digit is 0.
- In the first iteration, mod (the last digit of n) is added to digit, placing it in the units place.
- In the next iterations, digit is multiplied by 10, shifting the previous digits to the left (units to tens, tens to hundreds, etc.), and then mod is added to place the new digit in the correct position.
- This process ensures that each digit of n is reversed and placed correctly in digit.
