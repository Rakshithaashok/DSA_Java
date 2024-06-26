## Add Number Linked Lists [https://www.geeksforgeeks.org/problems/add-two-numbers-represented-by-linked-lists/1]

```
class Solution {
    // Function to add two numbers represented by linked list.
    static Node addTwoLists(Node num1, Node num2) {
        // Reverse both input linked lists
        num1 = reverse(num1);
        num2 = reverse(num2);
        
        Node dummy = new Node(-1); // Dummy node to build result list
        Node temp = dummy;
        int carry = 0;
        
        // Traverse both lists and add corresponding digits
        while (num1 != null || num2 != null || carry != 0) {
            int sum = carry;
            if (num1 != null) {
                sum += num1.data;
                num1 = num1.next;
            }
            if (num2 != null) {
                sum += num2.data;
                num2 = num2.next;
            }
            carry = sum / 10; // Determine carry for next addition
            int digit = sum % 10; // Digit to be added to the result list
            temp.next = new Node(digit);
            temp = temp.next;
        }
        
        // Reverse the result list to get the final sum
        Node result = reverse(dummy.next);
        
        // Remove leading zeros from the result
        result = removeLeadingZeros(result);
        
        return result;
    }
    
    // Function to reverse a linked list
    static Node reverse(Node head) {
        Node prev = null;
        Node current = head;
        Node next = null;
        
        while (current != null) {
            next = current.next;
            current.next = prev;
            prev = current;
            current = next;
        }
        
        return prev; // New head of the reversed list
    }
    
    // Function to remove leading zeros from the linked list
    static Node removeLeadingZeros(Node head) {
        // Traverse through any leading zeros
        while (head != null && head.data == 0 && head.next != null) {
            head = head.next;
        }
        return head;
    }
}
```
