## Palindrome String [https://www.geeksforgeeks.org/problems/palindrome-string0817/1]

Given a string S, check if it is palindrome or not.

## Example 1:

Input: S = "abba"

Output: 1

Explanation: S is a palindrome

## Example 2:

Input: S = "abc" 

Output: 0

Explanation: S is not a palindrome

## Your Task:

You don't need to read input or print anything. Complete the function isPalindrome()which accepts string S and returns an integer value 1 or 0.

Expected Time Complexity: O(Length of S)

Expected Auxiliary Space: O(1)

Constraints:  1 <= Length of S<= 2*105

## Code :

```
class Solution {
    int isPalindrome(String S) {
        // code here
        int i = 0;
        int j = S.length() - 1;
        while(i < j){
            if (S.charAt(i) == S.charAt(j))
            {
                i++;
                j--;
            }
            else{
                return 0;
            }
        }
        return 1;
    }
};
```

## Solution Explanation

This `Solution` class contains a method `isPalindrome` which checks if a given string `S` is a palindrome. Below is a step-by-step explanation of how the code works:

1. **Method Definition**:
    - The method `isPalindrome` is defined to take a `String` `S` as its parameter and returns an integer.

2. **Initialize Pointers `i` and `j`**:
    - Two integer pointers are initialized: `i` pointing to the start of the string (`i = 0`) and `j` pointing to the end of the string (`j = S.length() - 1`).

3. **Loop Through the String**:
    - A `while` loop runs as long as `i` is less than `j`: `while (i < j)`.
    - This ensures that the loop continues until the middle of the string is reached.

4. **Compare Characters**:
    - Inside the loop, the characters at indices `i` and `j` are compared: `if (S.charAt(i) == S.charAt(j))`.
    - If the characters are the same, it indicates that the current pair of characters is a palindrome, so the pointers are moved closer to the center: `i++` and `j--`.

5. **Return 0 for Mismatch**:
    - If the characters at indices `i` and `j` do not match, it means the string is not a palindrome, and the method returns `0`: `return 0`.

6. **Return 1 for Palindrome**:
    - If the loop completes without finding any mismatched characters, it means the string is a palindrome, and the method returns `1`: `return 1`.

### Example

For example, if the input string is `"radar"`, the steps will be:
- Initial string: `"radar"`
- Initial pointers: `i = 0`, `j = 4`
- 1st iteration: compare `S.charAt(0)` ('r') and `S.charAt(4)` ('r'), they match, increment `i` to `1`, decrement `j` to `3`
- 2nd iteration: compare `S.charAt(1)` ('a') and `S.charAt(3)` ('a'), they match, increment `i` to `2`, decrement `j` to `2`
- Loop terminates since `i` is no longer less than `j`
- No mismatches found, so the method returns `1`, indicating the string is a palindrome

### Time Complexity

The method efficiently checks for palindromes with a time complexity of O(n/2), which simplifies to O(n), where n is the length of the string. This ensures that each character is compared only once.

## Space Complexity 

O(1) - because no additional space is used.
