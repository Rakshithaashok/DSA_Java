```
class Solution
{
    public int find_median(int[] v)
    {
        // Code here
        int n = v.length;
        int div = n/2;
        Arrays.sort(v);
        if(v.length % 2 == 0){
            int avg = (v[div] + v[div - 1])/2;
            return avg;
        }
        return v[div];
    }
}
```
