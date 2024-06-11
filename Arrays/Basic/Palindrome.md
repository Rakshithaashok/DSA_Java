```
class GfG
{
	public static int palinArray(int[] a, int n)
           {
                  //add code here.
                  for(int i = 0; i < n; i++){
                      if(!isPalindrome(a[i])){
                          return 0;
                      }
                  }
                   return 1;
           }
    
    public static boolean isPalindrome(int a){
       int originalNum = a;
        int reverseNum = 0;
        while (a > 0) {
            int digit = a % 10;
            reverseNum = reverseNum * 10 + digit;
            a /= 10;
        }
        return originalNum == reverseNum;
    }
}
```
