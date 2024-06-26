## Add 1 to a number represented as linked list

A number n is represented in Linked List such that each digit corresponds to a node in linked list. You need to add 1 to it. Returns the head of the modified linked list. The driver code prints the number.

Note: The head represents the left-most digit of the number.

## Examples :

Input: LinkedList: 4->5->6

Output: 457

Explanation: 4->5->6 represents 456 and when 1 is added it becomes 457. 

Input: LinkedList: 1->2->3

Output: 124 

Explanation:  1->2->3 represents 123 and when 1 is added it becomes 124. 

Expected Time Complexity: O(n).

Expected Auxiliary Space: O(1).

Constraints:

1 <= n <= 1021

## Iterative Approach

```
class Solution
{
    public static Node addOne(Node head) 
    { 
        //code here.
        head = reverse(head);
        Node temp = head;
        int carry = 1;
        while(temp!=null && carry!=0){
            if(temp.data>=9){
                temp.data = 0;
                carry = 1;
            }
            else{
                temp.data+=1;
                carry = 0;
            }
            temp = temp.next;
        }
        head = reverse(head);
        if(carry==1){
            Node node = new Node(carry);
            node.next = head;
            head = node;
        }
        return head;
    }
    
    public static Node reverse(Node head){
        Node prev = null;
        Node curr = head;
        Node next = null;
        while(curr!=null){
            next = curr.next;
            curr.next = prev;
            prev = curr;
            curr = next;
        }
        return prev;
    }
}
```

**Time Complexity** :- O(3N) which is O(N)
**Space Complexity** :- O(1)

## Recursive Approach

```
class Solution
{
    public static Node addOne(Node head) 
    { 
        //code here.
        int carry = helper(head);
        if(carry == 1){
            Node node = new Node(carry);
            node.next = head;
            head = node;
        }
        return head;
    }
    public static int helper(Node temp){
        if(temp==null){
            return 1;
        }
        int carry = helper(temp.next);
        temp.data+=carry;
        if(temp.data<10)
            return 0;
        else{
            temp.data = 0;
            return 1;
        }
    }
}
```
**Time Complexity** ;- O(N)
**Space Complexity** :- O(N)


| Approach      | Pros                                                      | Cons                                                                   |
|---------------|-----------------------------------------------------------|------------------------------------------------------------------------|
| **Iterative** | - No extra space | - Tampering of data takes more time
| **Recursive** | - Addition done in place without modifying original data i.e No tampering| - Requires extra space for recursion stack|
