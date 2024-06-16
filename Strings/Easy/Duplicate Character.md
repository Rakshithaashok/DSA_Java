## Print all the duplicate characters in a string [https://www.geeksforgeeks.org/print-all-the-duplicates-in-the-input-string/]

Given a string S, the task is to print all the duplicate characters with their occurrences in the given string.

## Example:

Input: S = “geeksforgeeks”

Output:

e, count = 4

g, count = 2

k, count = 2

s, count = 2

## Method 1 - Find the duplicate characters in a string using Hashing

```
public class DuplicateCharacter {
    public static void main(String[] args){
        String s = "rakshitha";
        HashMap<Character, Integer> count = new HashMap<>();
        for(int i = 0; i < s.length(); i++){
            if(count.containsKey(s.charAt(i))){
                count.put(s.charAt(i), count.get(s.charAt(i)) + 1);
            }
            else{
                count.put(s.charAt(i), 1);
            }
        }
        System.out.println(s);
        System.out.println("Duplicate Character");
        for(Map.Entry<Character, Integer> mapElement : count.entrySet()){
            if(mapElement.getValue() > 1)
                System.out.println(mapElement.getKey()  + ", count = " + mapElement.getValue());
        }
    }
}
```

## Code Explanation 

This Java program identifies and counts duplicate characters in a given string. Below is a step-by-step explanation of how the code works:

### Code Explanation

1. **Class and Method Definition**:
    - The class `DuplicateCharacter` contains the `main` method, which is the entry point of the program.

2. **Input String**:
    - A string `s` is initialized with the value `"rakshitha"`.

3. **HashMap Initialization**:
    - A `HashMap` named `count` is created to store characters as keys and their counts as values.

4. **Iterate Through the String**:
    - A `for` loop runs from `i = 0` to `i < s.length()`, iterating through each character in the string.
    - For each character `s.charAt(i)`:
        - If the character is already present in the `count` map, its count is incremented by 1: `count.put(s.charAt(i), count.get(s.charAt(i)) + 1)`.
        - If the character is not present in the `count` map, it is added with a count of 1: `count.put(s.charAt(i), 1)`.

5. **Print Duplicate Characters**:
    - A `for` loop iterates through the entries of the `count` map:
        - For each entry, if the count of the character is greater than 1, it is printed as a duplicate character along with its count.

### Example

For the input string `"rakshitha"`, the program works as follows:
- Initial string: `"rakshitha"`
- The `count` map after processing:
    - `r` -> 1
    - `a` -> 2
    - `k` -> 1
    - `s` -> 1
    - `h` -> 2
    - `i` -> 1
    - `t` -> 1
- Duplicate characters found:
    - `a, count = 2`
    - `h, count = 2`

**Time Complexity:** O(N), where N = length of the string passed and it takes O(1) time to insert and access any element in an unordered map

**Auxiliary Space:** O(K), where K = size of the map (0<=K<=input_string_length), in worst case space will be O(N).

## Method 2 - Find the duplicate characters in a string using Sorting

```
public class DuplicateCharacter {
    public static void main(String[] args){
        String s = "rakshitha";
        int len = s.length();
        char[] CharArray = s.toCharArray();
        Arrays.sort(CharArray);
        String sortedstr = new String(CharArray);

        for(int i = 0; i < sortedstr.length(); i++){
            int count = 1;
            while(i < sortedstr.length() - 1 && sortedstr.charAt(i)==sortedstr.charAt(i+1)){
                count++;
                i++;
            }
            if(count > 1){
                System.out.println(sortedstr.charAt(i) + ", count = " + count);
            }
        }
    }
}
```

### Code Explanation

1. **Class and Method Definition**:
    - The class `DuplicateCharacter` contains the `main` method, which is the entry point of the program.

2. **Input String**:
    - A string `s` is initialized with the value `"rakshitha"`.

3. **Convert String to Character Array**:
    - The string `s` is converted to a character array `CharArray` using the `toCharArray()` method.

4. **Sort the Character Array**:
    - The character array `CharArray` is sorted using `Arrays.sort(CharArray)`. This brings identical characters together.

5. **Convert Sorted Array Back to String**:
    - The sorted character array is converted back to a string `sortedstr` using the `String` constructor.

6. **Initialize Loop Variables**:
    - The length of the string is stored in the variable `len`.

7. **Loop Through the Sorted String**:
    - A `for` loop runs from `i = 0` to `i < sortedstr.length()`, iterating through each character in the sorted string.
    - For each character at index `i`, initialize `count` to 1.
    - A `while` loop checks for consecutive identical characters:
        - If `sortedstr.charAt(i) == sortedstr.charAt(i+1)`, increment `count` and `i`.
    - After exiting the `while` loop, if `count` is greater than 1, it indicates a duplicate character:
        - The character and its count are printed to the console.

### Example

For the input string `"rakshitha"`, the program works as follows:
- Initial string: `"rakshitha"`
- The sorted string: `"aahhikrst"`
- The program then counts duplicate characters:
    - `a, count = 2`
    - `h, count = 2`

**Time Complexity:** O(N*logN), where n is the length of the string 
**Auxiliary Space:** O(1), if you observe we did not use any extra space.
