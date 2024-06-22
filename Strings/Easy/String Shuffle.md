## Check if a string is a valid shuffle of two distinct strings [https://www.programiz.com/java-programming/examples/check-valid-shuffle-of-strings]

```
public class ValidShuffle {
    public static void main(String[] args) {
        String first = "XY";
        String second = "12";
        String[] results = {"1XY2", "Y1X2", "Y21XX"};

        for(String result : results){
            if((checkLength(first,second,result) == true) && (checkString(first,second,result) == true)){
                System.out.println(result + " is a valid shuffle of " + first +" " + second);
            }
            else
            System.out.println(result + " is not a valid shuffle of " + first +" " + second);
        }
    }

    public static boolean checkLength(String first, String second, String result){
        if((first.length() + second.length()) != result.length())
            return false;
        return true;
    }

    public static boolean checkString(String first, String second, String result){
        first = sort(first);
        second = sort(second);
        result = sort(result);

        int i = 0, j = 0, k = 0;
        while(k < result.length()){
            if((i < first.length()) && (first.charAt(i) == result.charAt(k)))
                i++;
            else if((j < second.length()) && (second.charAt(j) == result.charAt(k)))
                j++;
            else
                return false;
            k++;
        }
        if(i < first.length() || j < second.length())
            return false;
        return true;
    }

    public static String sort(String str){
        char[] chararr =  str.toCharArray();
        Arrays.sort(chararr);

        str = String.valueOf(chararr);

        return str;
    }

}
```

**Time Complexity:** O(nlogn)

**Space Complexity:** O(n)
