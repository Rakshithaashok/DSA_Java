## Count triplets in a sorted doubly linked list whose sum is equal to a given value x [https://www.geeksforgeeks.org/count-triplets-sorted-doubly-linked-list-whose-sum-equal-given-value-x/]

## Naive Approach 
```
public void countTriplets(int sum){
        Node ptr1, ptr2, ptr3;
        int count = 0;
        for(ptr1 = head; ptr1 != null; ptr1 = ptr1.next){
            for(ptr2 = ptr1.next; ptr2!=null; ptr2 = ptr2 = ptr2.next){
                for(ptr3 = ptr2.next; ptr3!=null; ptr3=ptr3.next){
                    if((ptr1.val+ptr2.val+ptr3.val)==sum){
                        count++;
                    }
                }
            }
        }
        System.out.println(count);
    }
```

Time Complexity: O(n3) 

Auxiliary Space: O(1)

## Hashing Approach

```
public void countTriplets(int sum){
        Node ptr1,ptr2,ptr3;
        int count = 0;
        HashMap<Integer, Node> ref = new HashMap<>();
        for(ptr1 = head; ptr1!=null; ptr1=ptr1.next){
            ref.put(ptr1.val, ptr1);
        }
        for(ptr2 = head; ptr2!=null; ptr2 = ptr2.next){
            for(ptr3 = ptr2.next; ptr3!=null; ptr3= ptr3.next){
                int p_sum = ptr2.val + ptr3.val;
                if(ref.containsKey(sum - p_sum) && ref.get(sum - p_sum) != ptr2 && ref.get(sum - p_sum)!=ptr3){
                    count++;
                }
            }
        }
        System.out.println(count/3);
    }
```

Time Complexity: O(n2) 

Auxiliary Space: O(n)

## Efficient Approach(Use of two pointers):

```

```
