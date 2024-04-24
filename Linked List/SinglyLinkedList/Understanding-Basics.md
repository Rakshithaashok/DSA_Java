**SINGLY LINKED LIST**
```
public class LL {

    private Node head;
    private Node tail;
    private int size;
```
- This class represents the linked list data structure.
- It has private member variables head, tail, and size to manage the list.
- head points to the first node,
- tail points to the last node,
- size keeps track of the number of nodes in the list.

The constructor 
```
    public LL() {
        this.size = 0;
    }
```
- It sets the size of the linked list to 0.
- This means that when you create a new linked list object using LL list = new LL();, it starts with an empty list (zero elements).

**Why is it Important?** 

- Setting the size to 0 ensures that the linked list is properly initialized before any operations are performed on it.
- It provides a starting point for tracking the number of elements in the list.

```
    private class Node {
        private int value;
        private Node next;
```
- The nested Node class defines the individual nodes of the linked list.
```
        public Node(int value) {
            this.value = value;
        }
```
- This constructor creates a new node with the given value.
- It initializes the value of the node with the provided value.
- The next reference of the node remains uninitialized (null by default), indicating that this node is not linked to any other node.
```
        public Node (int value, Node next) {
            this.value = value;
            this.next = next;
        }
    }
```
- This constructor also creates a new node with the given value.
- Additionally, it specifies the next node to which this new node will be linked.
- It initializes both the value and next reference of the node with the provided values.
- This allows you to create nodes and establish their connections to other nodes in a single step.

**Inserting Node at First (head)**
![Singly Linked List Inserting Node at First](../Images/SinglyLinkedList_InsertAtFirst.png)

- First, a new node is created with the given value (val).
- The next reference of the newly created node is set to point to the current head of the linked list.
- The head reference of the linked list is updated to point to the newly inserted node.

- If the linked list was previously empty (meaning tail is null), the tail reference is also updated to point to the new node.
- This is because when the list is empty, the new node also becomes the last node in the list.
- Finally, the size of the linked list (size) is incremented by 1 to reflect the addition of the new node.
  
  ```
    public void insertFirst(int val) {
        Node node = new Node(val);
        node.next = head;
        head = node;

        if(tail == null) {
            tail = head;
        }

        size += 1;
    }
  ```
**Inserting Node at Last (Tail)**

![Singly Linked List Inserting Node at First](../Images/SinglyLinkedList_InsertAtLast.png)

- The method checks if the tail reference is null, indicating that the linked list is empty.
- If the list is empty, the method calls the insertFirst method to insert the new node at the beginning of the list.
- If the list is not empty, a new node is created with the provided value (val).
- The next reference of the current last node (tail) is updated to point to the new node.
- Now, the new node becomes the last node in the list.
- The size of the linked list is incremented by 1 to reflect the addition of the new node.

```
    public void insertLast(int val){
        if(tail == null) {
            insertFirst(val);
            return;
        }
        Node node = new Node(val);
        tail.next = node;
        tail = node;
        size+=1;
    }
```
  **Inserting Node by its Index Value**

  ![Singly Linked List Inserting Node at Index](../Images/SinglyLinkedList_InsertAtIndex.png)

- The method first checks if the specified index is 0
- In this case, it calls the insertFirst method to handle the insertion.
- Next, it checks if the specified index is equal to the current size of the list. If so, it calls the insertLast method to handle the insertion at the end of the list.

- The method iterates through the list using a temporary variable temp, starting from the head, until it reaches the node just before the insertion point (at index index - 1).
- Once the insertion point is found, a new node is created with the provided value (val), and its next reference is set to the node currently at the insertion point (temp.next).
- Then, the next reference of the previous node (temp) is updated to point to the new node, effectively inserting it into the list at the specified index.
  
```
    public void insert (int val, int index){
        if (index == 0){
            insertFirst(val);
            return;
        }
        if(index == size){
            insertLast(val);
            return;
        }
        Node temp = head;
        for(int i = 1; i < index; i++){
            temp = temp.next;
        }
        Node node = new Node(val, temp.next);
        temp.next = node;
    }
```
**Deleting Node at First (Head)**
- The method starts by storing the value of the current head node (head.value) in a variable val.
- This value will be returned later to the caller.
- The head reference is updated to point to the next node in the list (head = head.next).
- This effectively removes the first node from the list by skipping over it.

- If the head reference becomes null after removing the first node, it means that the list is now empty.
- In this case, the tail reference is also set to null. (Because in the linked list, if both head and tail were pointing to the same node(in case of size 1), then if head becomes null tail should also become null)

```
public int deleteFirst(){
        int val = head.value;
        head = head.next;
        if (head == null){
            tail = null;
        }
        size -- ;
        return val;
    }
```

**Deleting Node at Last(Tail)**
- The method checks if the size of the list is less than or equal to 1, indicating that there's either only one node or no node in the list.
- If the size is 1 or less, it means there's only one node or the list is empty. In such cases, it calls the deleteFirst method to handle the deletion.\

- If the size of the list is greater than 1, it means there are multiple nodes in the list.
- The method retrieves a reference to the second last node (secondLast) using the get method, passing size - 2 as the index. This is the node just before the last node.

- The value of the current tail node (tail.value) is stored in a variable val. This value will be returned later to the caller.
- The tail reference is updated to point to the secondLast node, effectively removing the last node from the list.
- The next reference of the new last node (tail.next) is set to null, breaking the link to the removed last node.
- Finally, the stored value of the deleted last node (val) is returned to the caller.

```
public int deleteLast(){
        if(size <=1 ){
            return deleteFirst();
        }
        Node secondLast = get(size - 2);
        int val = tail.value;
        tail = secondLast;
        tail.next = null;
        return val;
    }
```

**Deleting Node at Index**
- The method first checks if the specified index is 0, indicating the first node. If so, it calls the deleteFirst method to handle the deletion.
- Next, it checks if the specified index is equal to size - 1, indicating the last node. If so, it calls the deleteLast method to handle the deletion.

- If the index is neither 0 nor size - 1, it means the node to be deleted is an intermediate node.
- The method retrieves a reference to the node just before the node, to be deleted (prev) using the get method, passing index - 1 as the index.

- The value of the node to be deleted (prev.next.value) is stored in a variable val. This value will be returned later to the caller.
- The next reference of the previous node (prev.next) is updated to skip over the node to be deleted, pointing directly to the node after it.
- This effectively removes the node at the specified index from the list.
- Finally, the stored value of the deleted node (val) is returned to the caller.

```
public int delete(int index){
        if(index == 0){
            return deleteFirst();
        }
        if(index == size - 1){
            return deleteLast();
        }
        Node prev = get(index - 1);
        int val = prev.next.value;
        prev.next = prev.next.next;
        return val;
    }
```

***Finding a Node by its Value**
- The method initializes a temporary node node with the reference to the head node.
- This temporary node is used to traverse the linked list starting from the beginning.

- It enters a loop that continues until the temporary node (node) becomes null, indicating the end of the list.
- During each iteration, it checks if the value of the current node (node.value) matches the specified value (val).
- If a node with the desired value is found, the method immediately returns a reference to that node.

-If no node with the specified value is found after traversing the entire list, the method returns null.
- This indicates that the value does not exist in the linked list.

```
public Node find(int val){
        Node node = head;
        while (node!=null){
            if(node.value == val){
                return node;
            }
            node = node.next;
        }
        return null;
    }
```

**To get the Node By Index**
- The method initializes a temporary node node with the reference to the head node.
- This temporary node is used to traverse the linked list starting from the beginning.
- It enters a loop that iterates index times.
- During each iteration, it moves the temporary node (node) to the next node in the list by updating it to node.next.
- This process continues until the temporary node reaches the node at the specified index.
- Once the desired node is reached, the method returns a reference to that node (node).

```
public Node get(int index){
        Node node = head; //start from head and move ahead index times
        for(int i = 0; i < index; i++)
        {
            node = node.next;
        }
        return node; //returns reference pointer to that node
    }
```
**Displaying Node**

- The method starts by initializing a temporary variable temp with the reference to the head node.
- This variable is used to traverse the linked list, starting from the beginning.
- It enters a loop that continues until the temp variable becomes null, indicating the end of the list.
- During each iteration of the loop, it prints the value of the current node (temp.value) followed by a "->" to separate node values.
- After printing the value of the current node, the temp variable is updated to point to the next node in the list (temp = temp.next).
- This process continues until all nodes in the list have been traversed and printed.
- Once the loop exits (when temp becomes null), it prints "END" to indicate the end of the printed list.

```
    public void display() {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.value + " -> ");
            temp = temp.next;
        }
        System.out.println("END");
    }
}
```
**USAGE**
```
package src;

public class Main {
    public static void main(String[] args) {
        LL list = new LL();
        list.insertFirst(12);
        list.insertFirst(5);
        list.insertFirst(18);
        list.insertFirst(25);
        list.insertFirst(6);
        list.insertFirst(29);
        list.insertLast(99);
        list.insert(24, 2);
        list.display(); //Output:- 29 -> 6 -> 24 -> 25 -> 18 -> 5 -> 12 -> 99 -> END
    }
}

```
