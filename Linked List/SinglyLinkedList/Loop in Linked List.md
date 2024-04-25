**141 LINKED LIST CYCLE** 

**Detecting a Cycle** [LeetCode](https://leetcode.com/problems/linked-list-cycle/description/)

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

**IMPORTANT POINT TO NOTE**

 -  It's important to note that in the Floyd's Tortoise and Hare Algorithm, the difference in distances covered by the slow and fast pointers after each move should be 1 for effective loop detection.
- If the fast pointer were to move by a larger factor, such as 2 or 3, instead of 1, the pointers might not collide within the loop. This is because the difference in their positions may not shrink after each move, potentially causing the fast pointer to "jump over" the slow pointer without detection.
- By ensuring that the fast pointer moves exactly twice as fast as the slow pointer (i.e., the difference in their positions reduces by 1 after each move), we guarantee that if there's a loop, the fast pointer will eventually catch up to and collide with the slow pointer within the loop.

**Return Starting Point of Loop** [Leetcode](https://leetcode.com/problems/linked-list-cycle-ii/description/)
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
    public ListNode detectCycle(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        while (fast!=null && fast.next!=null){
            slow = slow.next;
            fast = fast.next.next;
            if(slow == fast){
                slow = head;
                while(slow!=fast){
                    slow = slow.next;
                    fast = fast.next;
                }
                return slow;
            }
        }
        return null;
    }
}
```
- We use the "Floyd's Tortoise and Hare Algorithm" to detect a cycle in the linked list.
- The slow pointer moves one step forward in each iteration (slow = slow.next), while the fast pointer moves two steps forward (fast = fast.next.next).
- If there's a cycle in the list, the two pointers will meet at some point (slow == fast).

- Once a cycle is detected, we reset the slow pointer to the head of the list while keeping the fast pointer where it is.
- Then, we move both pointers at the same pace (one step at a time) until they meet again.
- The meeting point of the slow and fast pointers is the node where the cycle begins.

- If a cycle is detected, the method returns the node where the cycle begins.
- If there's no cycle, the method returns null.

  **Point To Note**
- The distance from the slow pointer to the starting point of the cycle is equal to the distance from the starting point to the fast node inside the cycle.
- Similarly, the distance from the fast node inside the cycle to the starting point of the cycle (where the two pointers meet) is also equal.
- It ensures that when the slow and fast pointers are moved simultaneously after resetting, they will meet at the starting point of the cycle.
