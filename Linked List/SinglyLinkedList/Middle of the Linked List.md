**876 LEETCODE**

Given the head of a singly linked list, return the middle node of the linked list.
If there are two middle nodes, return the second middle node.

Example 1:

Input: head = [1,2,3,4,5]

Output: [3,4,5]

Explanation: The middle node of the list is node 3.

Example 2:

Input: head = [1,2,3,4,5,6]

Output: [4,5,6]

Explanation: Since the list has two middle nodes with values 3 and 4, we return the second one.

Constraints:

The number of nodes in the list is in the range [1, 100].

1 <= Node.val <= 100

**Solution 1**
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
    public ListNode middleNode(ListNode head) {
        ListNode val = head;
        int size = 0;
        while (val != null){
            size+=1;
            val = val.next;
        }
        if(size%2!=0){
            for(int i = 1; i <= size/2; i++){
                head = head.next;
            }
            return head;
        }
        for(int i = 1; i <= size/2; i++){
            head = head.next;
        }
        return head;
    }
}
```
- The method starts by initializing a temporary ListNode variable val with the reference to the head node.
- It also initializes an integer variable size to keep track of the size of the linked list.
- It then iterates through the linked list using a while loop, incrementing size for each node until reaching the end of the list (when val becomes null).
- After calculating the size of the list, the method enters a for loop to move head to the middle node.
- The loop iterates size / 2 times, effectively moving head halfway through the list.
- At the end of the loop, head points to the middle node of the list.
- Once the middle node is reached, the method returns a reference to that node (head).

**Solution 2**
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
    public ListNode middleNode(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        while(fast!=null && fast.next!=null){
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;
    }
}
```
- Two pointers, slow and fast, are initialized with the reference to the head node (head).
- Both pointers initially point to the head of the linked list.
- In each iteration of the while loop, the slow pointer moves one step forward (slow = slow.next), while the fast pointer moves two steps forward (fast = fast.next.next).
- This process continues until either the fast pointer reaches the end of the list (becomes null) or the fast.next pointer reaches the end of the list.
- At this point, the slow pointer will be pointing to the middle node of the list.
- Once the middle node is found, the method returns a reference to that node (slow).
