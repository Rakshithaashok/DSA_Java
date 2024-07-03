## Special array reversal [https://www.geeksforgeeks.org/problems/special-array-reversal2328/1]

```
class Solution
{
    public String reverse(String str)
    {
        //complete the function here
        char[] arr = str.toCharArray();
        int i = 0;
        int j = arr.length - 1;
        
        while (i < j) {
            // Check if both characters are alphabetic
            if (Character.isLetter(arr[i]) && Character.isLetter(arr[j])) {
                // Swap characters
                char temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
                i++;
                j--;
            }
            else {
                // If arr[i] is not a letter, move forward
                if (!Character.isLetter(arr[i])) {
                    i++;
                }
                // If arr[j] is not a letter, move backward
                if (!Character.isLetter(arr[j])) {
                    j--;
                }
            }
    }
    return new String(arr);
}
}
```
