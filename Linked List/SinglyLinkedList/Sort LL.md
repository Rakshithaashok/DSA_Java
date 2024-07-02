## Sort a linked list of 0s, 1s and 2s [https://www.geeksforgeeks.org/problems/given-a-linked-list-of-0s-1s-and-2s-sort-it/1]

## Approach 1

```
class Solution {
    // Function to sort a linked list of 0s, 1s and 2s.
    static Node segregate(Node head) {
        // add your code here
        Node temp = head;
        int c0 = 0;
        int c1 = 0;
        int c2 = 0;
        while(temp!=null){
            if(temp.data==0)
                c0++;
            else if(temp.data==1)
                c1++;
            else
                c2++;
            temp = temp.next;
        }
        temp = head;
        while(temp!=null){
            if(c0!=0){
                temp.data = 0;
                c0--;
            }
            else if(c1!=0){
                temp.data = 1;
                c1--;
            }
            else{
                temp.data = 2;
                c2--;
            }
            temp = temp.next;
        }
        return head;
    }
}
```
**Time Complexity** - O(2N) -> O(N)
**Space Complexity** - O(1)
