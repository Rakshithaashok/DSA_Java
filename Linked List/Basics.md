**Creating a Linked List**
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
  - 
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

    public void display() {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.value + " -> ");
            temp = temp.next;
        }
        System.out.println("END");
    }

}
