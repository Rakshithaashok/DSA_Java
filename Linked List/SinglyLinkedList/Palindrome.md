**Palindrome Linked List** [LeetCode](https://leetcode.com/problems/palindrome-linked-list/)

[Youtube](https://www.youtube.com/watch?v=lRY_G-u_8jk)

Given the head of a singly linked list, return true if it is a 
palindrome return true or false otherwise.
 
Example 1:

Input: head = [1,2,2,1]

Output: true

Example 2:

Input: head = [1,2]

Output: false

**Solution 1 -  Using Stack**

```
class Solution {
    public boolean isPalindrome(ListNode head) {
        Stack <Integer> stack = new Stack();
        ListNode temp = head;
        while(temp != null){
            stack.push(temp.val);
            temp = temp.next;
        }
        temp = head;
        while(temp != null){
            if(temp.val!=stack.pop()){
                return false;
            }
            temp = temp.next;
        }
        return true;
    }
}
```
- You initialize a stack to store the values of the linked list nodes.
- You also initialize a temporary pointer temp to traverse the linked list, starting from the head.
- You traverse the linked list with the temp pointer, pushing the values of each node onto the stack.
- After this loop, the stack will contain the values of the linked list nodes in the order they appear.
- You reset the temp pointer to the head of the linked list.
- You iterate through the linked list again with the temp pointer.
- In each iteration, you pop a value from the stack and compare it to the value of the current node pointed to by temp.
- If the values don't match, you immediately return false, indicating that the linked list is not a palindrome.
- After the loop, if all values matched without any mismatches, the function returns true, indicating that the linked list is a palindrome.
