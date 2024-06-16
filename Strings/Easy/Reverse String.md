## Reverse String [https://leetcode.com/problems/reverse-string/description/]

Write a function that reverses a string. The input string is given as an array of characters s.

You must do this by modifying the input array in-place with O(1) extra memory.

## Example 1:

Input: s = ["h","e","l","l","o"]

Output: ["o","l","l","e","h"]

## Example 2:

Input: s = ["H","a","n","n","a","h"]

Output: ["h","a","n","n","a","H"]
 
## Constraints:

1 <= s.length <= 105

s[i] is a printable ascii character.

## Code

```
class Solution {
    public void reverseString(char[] s) {
        int j = s.length - 1; 
        for(int i = 0; i < s.length/2; i++){
            char temp = s[j]; 
            s[j] = s[i];
            s[i] = temp;
            j--; 
        }
    }
}
```

## Solution Explanation

This `Solution` class contains a method `reverseString` which reverses a given array of characters in place. Below is a step-by-step explanation of how the code works:

1. **Method Definition**:
    - The method `reverseString` is defined to take a character array `s` as its parameter.

2. **Initialize Pointer `j`**:
    - An integer `j` is initialized to point to the last index of the array: `j = s.length - 1`.

3. **Loop Through Half of the Array**:
    - A `for` loop runs from the start of the array to the middle: `for (int i = 0; i < s.length / 2; i++)`.
    - The reason for iterating only up to `s.length / 2` is to ensure that each element from the start is swapped with the corresponding element from the end without re-swapping.

4. **Swap Elements**:
    - Inside the loop, a temporary variable `temp` is used to hold the value of the element at index `j`: `char temp = s[j]`.
    - The element at index `j` is then replaced with the element at index `i`: `s[j] = s[i]`.
    - The element at index `i` is replaced with the value stored in `temp`, completing the swap: `s[i] = temp`.

5. **Decrement Pointer `j`**:
    - The pointer `j` is decremented to move towards the start of the array: `j--`.
    - This ensures that in the next iteration, the next pair of elements are swapped.

6. **In-Place Reversal**:
    - The process continues until the loop has iterated through half of the array, at which point the array is fully reversed.
    - The reversal is done in place, meaning no additional space is used beyond the temporary variable `temp`.

### Example

For example, if the input array is `['h', 'e', 'l', 'l', 'o']`, the steps will be:
- Initial array: `['h', 'e', 'l', 'l', 'o']`
- After 1st iteration (i = 0, j = 4): `['o', 'e', 'l', 'l', 'h']`
- After 2nd iteration (i = 1, j = 3): `['o', 'l', 'l', 'e', 'h']`
- Loop terminates since `i < s.length / 2` is no longer true, resulting in the final reversed array: `['o', 'l', 'l', 'e', 'h']`.

This efficient method ensures that the string is reversed with a time complexity of O(n/2), which simplifies to O(n), where n is the length of the array.

Space complexity is O(1) because we are not using any extra place and swapping elements in-place.
