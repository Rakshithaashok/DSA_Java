## Split a Circular Linked List into two halves [https://www.geeksforgeeks.org/problems/split-a-circular-linked-list-into-two-halves/1]

```
class gfg
{
        // Function  to split a circular LinkedList
	    void splitList(circular_LinkedList list)
        {
             //DO NOT REMOVE THESE 3 LINES
             Node head=list.head;
             Node head1=null;
             Node head2=null;
             
             if(head==null || head.next==null){
                 head1 = head;
                 if(head1!=null){
                     head1.next = head1;
                 }
                 head2 = null;
                 list.head1 = head1;
                 list.head2 = head2;
                 return;
             }
             
             Node slow = head;
             Node fast = head;
             
             while(fast.next!=head && fast.next.next!=head){
                 slow = slow.next;
                 fast = fast.next.next;
             }
             
             head1 = head;
             head2 = slow.next;
             slow.next = head1;
             Node current = head2;
             while(current.next!=head){
                 current = current.next;
             }
             current.next = head2;
             
             
             //Modify these head1 and head2 here, head is the starting point of our original linked list.    
             
             
             //DO NOT REMOVE THESE 2 LINES
             list.head1=head1;
             list.head2=head2;
	 }
}
```
