**Given Array of size n and a number k, find all elements that appear more than n/k times**

Given an array of size n and an integer k, find all elements in the array that appear more than n/k times. 

Examples:

Input: arr[] = {3, 1, 2, 2, 1, 2, 3, 3}, k = 4

Output: {2, 3}

Explanation: Here n/k is 8/4 = 2, therefore 2 appears 3 times in the array that is greater than 2 and 3 appears 3 times in the array that is greater than 2

Input: arr[] = {9, 8, 7, 9, 2, 9, 7}, k = 3

Output: {9}

Explanation: Here n/k is 7/3 = 2, therefore 9 appears 3 times in the array that is greater than 2.

**Find all elements that appear more than n/k times using Hashing:**
The idea is to pick all elements one by one. For every picked element, count its occurrences by traversing the array, if count becomes more than n/k, then print the element.

Follow the steps below to solve the problem:

- First, make a frequency map of all the elements in the array
- Then traverse the map and check the frequency of every element
- If the frequency is greater than n/k then print the element.

```
public class MorethanNbyK {
    public static void main(String[] args){
        int[] arr = {1, 1, 2, 2, 3, 5, 4,
                2, 2, 3, 1, 1, 1};
        int K = 4;
        morethanNbyK(arr, arr.length, K);
    }

    public static void morethanNbyK(int[] arr, int N, int K){
        int target = N/K;
        HashMap<Integer, Integer> elements = new HashMap<>();

        for(int i : arr){
            elements.put(i, elements.getOrDefault(i, 0) +1);
        }

        for(Map.Entry <Integer, Integer> entry : elements.entrySet()){
            if(entry.getValue() > target){
                System.out.println(entry.getKey());
            }
        }
    }
}   
```
Time Complexity: O(N), Traversing the array of size N.

Auxiliary Space: O(N), Space occupied by the hashmap

**Moore Voting Algorithm** 

Youtube - [https://youtu.be/n5QY3x_GNDg?si=p8n4P-2mbVFL2v96]

```
public class MorethanNbyK {


    public static void main(String[] args){
        int[] arr = { 4, 5, 6, 7, 8, 4, 4 };
        int K = 3;
        int target = arr.length/K; // 7/3 = 2
        int me = majorityElement(arr);
        int count = ismajority(arr, me);
        if(count > target)
            System.out.println(me);
        else
            System.out.println("No element Present");
    }

    public static int majorityElement(int[] arr){
        int me = 0;
        int count = 0;
        for(int i : arr){
            if(count == 0){
                me = i;
                count = 1;
            }
            else if(i == me){
                count++;
            }
            else if(i != me){
                count--;
            }
        }
        return me;
    }

    public static int ismajority(int[] arr, int majorityelement){
        int count = 0;
        for(int i = 0; i < arr.length; i++){
            if(arr[i] == majorityelement){
                count++;
            }
        }
        return count;
    }
}
```

Time Complexity - O(n) 

we are using 2 loops so which makes it O(2n), ignoring constants gives O(n)

Space Complexity - O(1)
