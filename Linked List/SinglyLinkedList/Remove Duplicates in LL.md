## Remove Duplicates from a Sorted Linked List [https://www.geeksforgeeks.org/problems/remove-duplicate-element-from-sorted-linked-list/1]

Given a singly linked list consisting of N nodes. The task is to remove duplicates (nodes with duplicate values) from the given list (if exists).
Note: Try not to use extra space. The nodes are arranged in a sorted way.

## Example 1:

Input:

LinkedList: 2->2->4->5

Output: 2 4 5

Explanation: In the given linked list 

2 ->2 -> 4-> 5, only 2 occurs more 

than 1 time. So we need to remove it once.

Example 2:

Input:

LinkedList: 2->2->2->2->2

Output: 2

Explanation: In the given linked list 

2 ->2 ->2 ->2 ->2, 2 is the only element

and is repeated 5 times. So we need to remove

any four 2.

## Your Task:

The task is to complete the function removeDuplicates() which takes the head of input linked list as input. The function should remove the duplicates from linked list and return the head of the linkedlist.

Expected Time Complexity : O(N)

Expected Auxilliary Space : O(1)

Constraints:

1 <= Number of nodes <= 105

## Code

```
class GfG
{
    //Function to remove duplicates from sorted linked list.
    Node removeDuplicates(Node head)
    {
	// Your code here
	    if(head==null || head.next==null)
	        return head;
	   Node temp = head;
	   while(temp.next!=null){
	       if(temp.data == temp.next.data){
	           temp.next = temp.next.next;
	       }
	       else{
	           temp = temp.next;
	       }
	   }
	   return head;
    }
}
```

## Remove duplicates from an unsorted linked list [https://www.geeksforgeeks.org/problems/remove-duplicates-from-an-unsorted-linked-list/1]

Given an unsorted linked list of N nodes. The task is to remove duplicate elements from this unsorted Linked List. When a value appears in multiple nodes, the node which appeared first should be kept, all others duplicates are to be removed.

## Example 1:

Input:

N = 4

value[] = {5,2,2,4}

Output: 5 2 4

Explanation:Given linked list elements are

5->2->2->4, in which 2 is repeated only.

So, we will delete the extra repeated

elements 2 from the linked list and the

resultant linked list will contain 5->2->4

## Example 2:

Input:

N = 5

value[] = {2,2,2,2,2}

Output: 2

Explanation:Given linked list elements are

2->2->2->2->2, in which 2 is repeated. So,

we will delete the extra repeated elements

2 from the linked list and the resultant

linked list will contain only 2.

## Your Task:

You have to complete the method removeDuplicates() which takes 1 argument: the head of the linked list.  Your function should return a pointer to a linked list 

with no duplicate element.

Expected Time Complexity: O(N)

Expected Auxiliary Space: O(N)

Constraints:

1 <= size of linked lists <= 106

0 <= numbers in list <= 104

## Code 

```
class Solution
{
    //Function to remove duplicates from unsorted linked list.
    public Node removeDuplicates(Node head) 
    {
         // Your code here
        HashSet <Integer> ans = new HashSet<>();
        Node prev = null;
        Node curr = head;
        while(curr!=null){
            if(ans.contains(curr.data)){
                prev.next = curr.next;
            }
            else{
                ans.add(curr.data);
                prev = curr;
            }
            curr = curr.next;
        }
        return head;
    }
}
```
## Remove all occurences of duplicates in a linked list [https://www.geeksforgeeks.org/problems/remove-all-occurences-of-duplicates-in-a-linked-list/1]

```
class Solution {
    public Node removeAllDuplicates(Node head) {
        // code here
        if(head==null || head.next== null){
            return head;
        }
        Node dummy = new Node(-1);
        dummy.next = head;
        
        Node prev = dummy;
        Node curr = head;
        
        
        
        while(curr!=null){
            boolean isDuplicate = false;
            while(curr.next!=null && curr.data==curr.next.data){
                isDuplicate = true;
                curr = curr.next;
            }
            if(isDuplicate){
                prev.next = curr.next;
            }
            else{
                prev = prev.next;
            }
            curr = curr.next;
        }
        return dummy.next;
    }
}
```
