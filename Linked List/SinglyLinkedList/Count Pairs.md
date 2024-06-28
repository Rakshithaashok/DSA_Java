## Count Pairs whose sum is equal to X [https://www.geeksforgeeks.org/problems/count-pairs-whose-sum-is-equal-to-x/1]

```
class Solution {

    public static int countPairs(LinkedList<Integer> head1, LinkedList<Integer> head2,
                          int x) {
        // add your code here
        int count = 0;
        HashSet<Integer> set = new HashSet<>();

        // Add all elements of the first list to the set
        for (int num : head1) {
            set.add(num);
        }

        // For each element in the second list, check if (x - element) is in the set
        for (int num : head2) {
            if (set.contains(x - num)) {
                count++;
            }
        }

        return count;
    }
}
```


