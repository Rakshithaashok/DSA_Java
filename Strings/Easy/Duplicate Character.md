## Print all the duplicate characters in a string [https://www.geeksforgeeks.org/print-all-the-duplicates-in-the-input-string/]

Given a string S, the task is to print all the duplicate characters with their occurrences in the given string.

## Example:

Input: S = “geeksforgeeks”

Output:

e, count = 4

g, count = 2

k, count = 2

s, count = 2

**Find the duplicate characters in a string using Hashing**

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
