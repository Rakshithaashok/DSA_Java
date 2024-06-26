## Intersection Point in Y Shaped Linked Lists [https://www.geeksforgeeks.org/problems/intersection-point-in-y-shapped-linked-lists/1]

```
class Intersect {
    // Function to find intersection point in Y shaped Linked Lists.
    int intersectPoint(Node head1, Node head2) {
        if (head1 == null || head2 == null)
            return -1;
        
        Node temp1 = head1;
        Node temp2 = head2;
        
        while (temp1 != temp2) {
            temp1 = (temp1 == null) ? head2 : temp1.next;
            temp2 = (temp2 == null) ? head1 : temp2.next;
            
            // If they meet at an intersection, return the data of the intersection node
            if (temp1 == temp2 && temp1 != null)
                return temp1.data;
        }
        
        // If no intersection found, return -1
        return -1;
    }
}
```
