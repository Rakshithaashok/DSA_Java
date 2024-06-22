# String Rotation Check [https://www.geeksforgeeks.org/a-program-to-check-if-strings-are-rotations-of-each-other/]

This Java program checks if one string (`s2`) is a rotation of another string (`s1`).

Given a string s1 and a string s2, write a function to check whether s2 is a rotation of s1. 

## Naive Approach: 

Follow the given steps to solve the problem

- Find all the positions of the first character of the original string in the string to be checked.
- For every position found, consider it to be the starting index of the string to be checked.
- Beginning from the new starting index, compare both strings and check whether they are equal or not.
- (Suppose the original string to is s1, string to be checked to be s2,n is the length of strings and j is the position of the first character of s1 in s2, then for i < (length of original string) , check if s1[i]==s2[(j+1)%n). Return false if any character mismatch is found, else return true.
- Repeat 3rd step for all positions found.

## Examples: 

Input: S1 = ABCD, S2 = CDAB

Output: Strings are rotations of each other

Input: S1 = ABCD, S2 = ACBD

Output: Strings are not rotations of each other

## Code

```
public class StringRotation {
    public static void main(String[] args){
        String s1 = "abcd";
        String s2 = "acbd";

        if(s1.length() != s2.length()){
            System.out.println("s2 is not a rotation of s1");
        }
        else{
            ArrayList<Integer> indexes = new ArrayList<>();
            char firstChar = s1.charAt(0);
            for(int i = 0; i < s1.length(); i++){
                if(s2.charAt(i) == firstChar){
                    indexes.add(i);
                }
            }
            boolean isRotation = false;

            for(int index : indexes){
                isRotation = checkString(s1, s2, index);

                if(isRotation)
                    break;
            }

            if(isRotation)
                System.out.println("s2 is rotation of s1");
            else
                System.out.println("s2 is not rotation of s1");
        }
    }

    public static boolean checkString(String s1, String s2, int index){
        for(int i = 0; i < s1.length(); i++){
            if(s1.charAt(i) != s2.charAt((index + i) % s1.length())){
                return false;
            }
        }
        return true;
    }
}
```

## Explanation

- Initial Check:

```
if(s1.length() != s2.length()){
    System.out.println("s2 is not a rotation of s1");
}
```

- Find Occurrences of the First Character

```
  ArrayList<Integer> indexes = new ArrayList<>();
  char firstChar = s1.charAt(0);
  for(int i = 0; i < s1.length(); i++){
    if(s2.charAt(i) == firstChar){
        indexes.add(i);
    }
}
```

Finds all positions in s2 where the first character of s1 appears.

- Check for Rotation:

```
boolean isRotation = false;

for(int index : indexes){
    isRotation = checkString(s1, s2, index);

    if(isRotation)
        break;
}

```

Iterates over each found index and checks if starting from that index s2 can be a rotation of s1.

Breaks the loop if a valid rotation is found.

- Output the Result:

```
if(isRotation)
    System.out.println("s2 is rotation of s1");
else
    System.out.println("s2 is not rotation of s1");
```

Prints whether s2 is a rotation of s1 based on the isRotation flag.

- Check String Method:

```
public static boolean checkString(String s1, String s2, int index){
    for(int i = 0; i < s1.length(); i++){
        if(s1.charAt(i) != s2.charAt((index + i) % s1.length())){
            return false;
        }
    }
    return true;
}
```

Checks if s2 starting from a given index matches s1 character by character, using modulo operation to wrap around s2.

## Example

For s1 = "abcd" and s2 = "acbd", the program will output:

```
s2 is not rotation of s1
```

For s1 = "abcd" and s2 = "cdab", the program will output:

```
s2 is rotation of s1
```


Time Complexity: O(N) in the worst case, where n is the length of the string.

Auxiliary Space: O(n)

## Program to check if strings are rotations of each other or not using queue:


Follow the given steps to solve the problem

- If the size of both strings is not equal, then it can never be possible.
- Push the original string into a queue q1.
- Push the string to be checked inside another queue q2.
- Keep popping q2‘s and pushing it back into it till the number of such operations is less than the size of the string.
- If q2 becomes equal to q1 at any point during these operations, it is possible. Else not.

```
public class StringRotation {
    public static void main(String[] args) {
        String s1 = "abcd";
        String s2 = "bcda";

        if(checkRotation(s1, s2)){
            System.out.println("s2 is rotation of s1");
        }
        else
            System.out.println("s2 is not rotation of s1");
    }

    public static boolean checkRotation(String s1, String s2){
         if(s1.length()!=s2.length())
             return false;
         else{
             Queue<Character> q1 = new LinkedList<>();
             Queue<Character> q2 = new LinkedList<>();
             for(int i = 0; i < s1.length(); i++){
                 q1.add(s1.charAt(i));
                 q2.add(s2.charAt(i));
             }

             int k = s2.length();
             while (k > 0){
                 k--;
                 char ch = q2.peek();
                 q2.remove();
                 q2.add(ch);
                 if(q1.equals(q2))
                     return true;
             }
         }
         return false;
    }
}
```
## Detailed Iteration

- Initial Queues:

q1: ['A', 'A', 'C', 'D']

q2: ['A', 'C', 'D', 'A']

- Iteration 1:

k = 4

Rotate q2: Remove A from front and add it to the back.

q2: ['C', 'D', 'A', 'A']

Compare q1 and q2: ['A', 'A', 'C', 'D'] ≠ ['C', 'D', 'A', 'A']

- Iteration 2:

k = 3

Rotate q2: Remove C from front and add it to the back.

q2: ['D', 'A', 'A', 'C']

Compare q1 and q2: ['A', 'A', 'C', 'D'] ≠ ['D', 'A', 'A', 'C']

- Iteration 3:

k = 2

Rotate q2: Remove D from front and add it to the back.

q2: ['A', 'A', 'C', 'D']

Compare q1 and q2: ['A', 'A', 'C', 'D'] == ['A', 'A', 'C', 'D']

The queues are equal, so the function returns true.

Time Complexity: O(n^2)

Space Complexity: O(n)

## Efficient Approach: 

Follow the given steps to solve the problem

- Create a temp string and store concatenation of str1 to str1 in temp, i.e temp = str1.str1
- If str2 is a substring of temp then str1 and str2 are rotations of each other.

## Example: 

str1 = “ABACD”, str2 = “CDABA”

temp = str1.str1 = “ABACDABACD”

Since str2 is a substring of temp, str1 and str2 are rotations of each other.

## Code

```
class StringRotation {
    public static void main(String[] args) {
        String s1 = "abcd";
        String s2 = "bcda";

        if (checkString(s1, s2))
            System.out.println("s2 is rotation of s1");
        else
            System.out.println("s2 is not rotation of s1");
    }

    public static boolean checkString(String s1, String s2) {
         return ((s1.length()==s2.length()) && ((s1+s2).indexOf(s2))!=-1);
    }
}
```

## Explanation

- Concatenation:

(str1 + str1) concatenates str1 with itself. For example, if str1 is "AACD", then (str1 + str1) becomes "AACDAACD".
- indexOf Method:

The indexOf method is called on the concatenated string (str1 + str1) with the argument str2.

This method returns the index at which the specified substring str2 first occurs in the concatenated string (str1 + str1).

If str2 is not found, indexOf returns -1.

For example:
If str1 = "AACD" and str2 = "ACDA", (str1 + str1) becomes "AACDAACD".
Calling "AACDAACD".indexOf("ACDA") returns 2, as "ACDA" starts at index 2 in the concatenated string.

- Comparison:

- If the index returned by indexOf is not -1, it means that str2 is found in the concatenated string (str1 + str1).
- This implies that str2 is indeed a rotation of str1, as it is found within the concatenated string obtained by rotating str1.

Time Complexity: O(n)

Space Complexity: O(n)

