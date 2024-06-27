## Check If Circular Linked List [https://www.geeksforgeeks.org/problems/circular-linked-list/1]

```
class GfG
{
    boolean isCircular(Node head)
    {
	// Your code here
	    if(head==null || head.next == null)
	        return false;
	    Node temp = head;
	    do {
	        temp = temp.next;
	        if(temp == head)
	            return true;
	    }while(temp!=head && temp!=null);
	    return false;
    }
}
```
