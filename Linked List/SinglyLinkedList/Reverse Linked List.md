**206 Reverse Linked List**

Given the head of a singly linked list, reverse the list, and return the reversed list.

Example 1:

Input: head = [1,2,3,4,5]

Output: [5,4,3,2,1]

Example 2:

Input: head = [1,2]

Output: [2,1]

Example 3:

Input: head = []

Output: []
 
Constraints:

The number of nodes in the list is the range [0, 5000].
-5000 <= Node.val <= 5000

```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode current = head; 
        while (current!=null){
            ListNode next = current.next; 
            current.next = prev; 
            prev = current; 
            current = next; 
        }
        return prev;
    }
}
```
**Initial State:**
```
1 -> 2 -> 3 -> 4 -> 5 -> null
^
|
head
prev = null
current = head
```
**Iteration 1:**
- Hold the Previous Node (prev):
- prev = null
- Flip the Current Node (current):
- Disconnect current node from next and point it to previous.
- current.next = prev
```
1 <- 2 -> 3 -> 4 -> 5 -> null
^    ^
|    |
prev current
```
- Move to the Next Node (current):
- prev = current
- current = current.next
```
1 <- 2 -> 3 -> 4 -> 5 -> null
     ^    ^
     |    |
    prev current
```
**Iteration 2:**
- Hold the Previous Node (prev):
- prev = 1
- Flip the Current Node (current):
- Disconnect current node from next and point it to previous.
- current.next = prev
```
1 <- 2 <- 3 -> 4 -> 5 -> null
         ^    ^
         |    |
        prev current
```
- Move to the Next Node (current):
- prev = current
- current = current.next
```
1 <- 2 <- 3 -> 4 -> 5 -> null
                ^    ^
                |    |
               prev current
```
**Iterations 3, 4, and 5:**
- These iterations follow the same pattern, moving prev and current to the next nodes and flipping the direction of the connections.

**Final State:**
- After iterating through all nodes:
```
1 <- 2 <- 3 <- 4 <- 5 -> null
                         ^
                         |
                       head (prev)
```
**Returning the New Beginning:**
The prev pointer is now holding onto the last node, which is the new beginning of the reversed list. So, we return prev.

**Conclusion:**
The original linked list 1 -> 2 -> 3 -> 4 -> 5 has been successfully reversed to 5 -> 4 -> 3 -> 2 -> 1.

![Image1](../Images/reverseimage1.png)

![Image1](../Images/reverseimage2.png)

