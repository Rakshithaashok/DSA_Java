## Sort 0s, 1s and 2s without Sorting Algorithm[https://www.geeksforgeeks.org/problems/sort-an-array-of-0s-1s-and-2s4231/1]

```
class Solution
{
    public static void sort012(int a[], int n)
    {
        // code here
        int c0 = 0;
        int c1 = 0;
        int c2 = 0;
        for(int i : a){
            if(i==0)
                c0++;
            else if(i==1)
                c1++;
            else
                c2++;
        }
        for(int i = 0; i < a.length; i++){
            if(c0!=0){
                a[i] = 0;
                c0--;
            }
            else if(c1!=0){
                a[i] = 1;
                c1--;
            }
            else{
                a[i] = 2;
                c2--;
            }
        }
    }
}
```
