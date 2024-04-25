**141 LINKED LIST CYCLE** [LeetCode](https://leetcode.com/problems/linked-list-cycle/description/)

Given head, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that tail's next pointer is connected to. Note that pos is not passed as a parameter.

Return true if there is a cycle in the linked list. Otherwise, return false.

Example 1:

Input: head = [3,2,0,-4], pos = 1

Output: true

Explanation: There is a cycle in the linked list, where the tail connects to the 1st node (0-indexed).

Example 2:

Input: head = [1,2], pos = 0

Output: true

Explanation: There is a cycle in the linked list, where the tail connects to the 0th node.

Example 3:


Input: head = [1], pos = -1

Output: false

Explanation: There is no cycle in the linked list. 

Constraints:

The number of the nodes in the list is in the range [0, 104].
-105 <= Node.val <= 105
pos is -1 or a valid index in the linked-list.

```
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        while (fast!=null && fast.next!=null){
            slow = slow.next;
            fast = fast.next.next;
            if(slow == fast){
                return true;
            }
        }
        return false;
    }
}
```
- Two pointers, slow and fast, are initialized with the reference to the head node (head).
- Both pointers initially point to the head of the linked list.

- The method uses a classic approach called the "slow and fast pointers" (TortoiseHaire Method) technique to detect a cycle in the linked list.
- In each iteration of the while loop, the slow pointer moves one step forward (slow = slow.next), while the fast pointer moves two steps forward (fast = fast.next.next).
- If there is a cycle in the list, eventually the fast pointer will catch up to the slow pointer, indicating the presence of a cycle. In this case, slow and fast will point to the same node (slow == fast), and the method returns true.

- If the while loop completes without finding a cycle (i.e., if fast becomes null or fast.next becomes null), it means there is no cycle in the list, and the method returns false.

**FIND LENGTH OF LOOP**
[CodingNinjas](https://www.naukri.com/code360/problems/find-length-of-loop_8160455?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf)

You’re given a linked list. The last node might point to null, or it might point to a node in the list, thus forming a cycle.

Find out whether the linked list has a cycle or not, and the length of the cycle if it does.

If there is no cycle, return 0, otherwise return the length of the cycle.

Example:

Input: Linked List: 4 -> 10 -> 3 -> 5 -> 10(at position 2)

Output: Length of cycle = 3

Explanation: The cycle is 10, 3, 5.

```
public class Solution
{
    public static int lengthOfLoop(Node head) {
        // Write your code here
        Node slow = head;
        Node fast = head;
        while(fast!=null && fast.next!=null){
            slow = slow.next;
            fast = fast.next.next;
            if(slow == fast){
                int count = 1;
                fast = fast.next;
                while(slow!=fast){
                    count++;
                    fast=fast.next;
                }
                return count;
            }
        }
        return 0;
    }
}
```
- Two pointers, slow and fast, are initialized with the reference to the head node (head).
- Both pointers initially point to the head of the linked list.

- The method uses the "slow and fast pointers" technique to detect a loop in the linked list.
- In each iteration of the while loop, the slow pointer moves one step forward (slow = slow.next), while the fast pointer moves two steps forward (fast = fast.next.next).
- If there is a loop in the list, eventually the slow pointer will meet the fast pointer, indicating the presence of a loop (slow == fast).
- 
- Once a loop is detected, the method initializes a count variable to 1 (since we've already detected one node in the loop).
- It moves the fast pointer one step forward (fast = fast.next) and increments the count until the fast pointer meets the slow pointer again, completing one loop cycle.
- The value of count represents the length of the loop, so it is returned.

- If the while loop completes without finding a loop (i.e., if fast becomes null or fast.next becomes null), it means there is no loop in the list, and the method returns 0.
