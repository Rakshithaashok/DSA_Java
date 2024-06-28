## Reverse a Doubly Linked List [https://www.geeksforgeeks.org/problems/reverse-a-doubly-linked-list/1]

```
public static Node reverseDLL(Node  head)
{
    //Your code here
    Node prev = null;
    Node curr = head;
    Node next = null;
    while(curr!=null){
        next = curr.next;
        curr.next = prev;
        curr.prev = next;
        prev = curr;
        curr = next;
    }
    return prev;
}
```
