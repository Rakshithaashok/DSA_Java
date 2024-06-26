## Intersection Sorted Linked Lists [https://www.geeksforgeeks.org/problems/intersection-of-two-sorted-linked-lists/1]

```
class Solution {
    public static Node findIntersection(Node head1, Node head2) {
        Node dummy = new Node(-1); // Dummy node to build result list
        Node current = dummy;
        Node ptr1 = head1;
        Node ptr2 = head2;
        
        // Traverse both lists while both pointers are not null
        while (ptr1 != null && ptr2 != null) {
            if (ptr1.data == ptr2.data) {
                current.next = new Node(ptr1.data); // Add common element to result list
                current = current.next; // Move current pointer forward
                ptr1 = ptr1.next; // Move ptr1 forward
                ptr2 = ptr2.next; // Move ptr2 forward
            } else if (ptr1.data < ptr2.data) {
                ptr1 = ptr1.next; // Move ptr1 forward
            } else {
                ptr2 = ptr2.next; // Move ptr2 forward
            }
        }
        
        return dummy.next; // Return the head of the result list
    }
}
```
