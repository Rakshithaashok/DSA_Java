## Move Last Element to Front of a Linked List [https://www.geeksforgeeks.org/problems/move-last-element-to-front-of-a-linked-list/1?page=4&category=Linked%20List&sortBy=submissions]

```
class Solution {
    public static Node moveToFront(Node head) {
        // code here
        if(head == null || head.next==null)
            return head;
        Node temp = head;
        while(temp.next.next!=null){
            temp = temp.next;
        }
        Node tail = temp.next;
        temp.next = null;
        tail.next = head;
        head = tail;
        return head;
    }
}
```
