## Find pairs with given sum in doubly linked list [https://www.geeksforgeeks.org/find-pairs-given-sum-doubly-linked-list/]

```
public void FindPairs(int sum){
        Node first = head;
        Node second = head;
        boolean found = false;
        while(second.next!=null){
            second = second.next;
        }
        while(first!=second && second.next != first) {
            if ((first.val + second.val) == sum) {
                System.out.println("Pairs = ( " + first.val + " " + second.val + " )");
                first = first.next;
                second = second.prev;
                found = true;
            } else {
                if ((first.val + second.val) < sum) {
                    first = first.next;
                } else {
                    second = second.prev;
                }
            }
        }
        if(found==false){
            System.out.println("No pairs found");
        }
    }
```
