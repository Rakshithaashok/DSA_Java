**In-place**
```
An in-place algorithm modifies the original data structure (in this case, the array) to achieve the desired outcome.
It doesn't require creating a new data structure to store the reversed elements.
The original data structure is manipulated directly through operations like swapping elements.
```
**Non-in-place**
```
A non-in-place algorithm creates a new data structure to store the result.
It iterates through the original data structure, copying elements to the new structure in the reversed order.
The original data structure remains unchanged.
```

**Array Reverse Using an Extra Array (Non In-place)**

```
class ReverseArray {

    // Method to reverse the given array
    public static void reverseArray(int[] arr) {
        // Create a new array to hold the reversed elements
        int[] reversedArray = new int[arr.length];
        
        // Loop through the original array and fill the reversedArray
        for (int i = 0; i < reversedArray.length; i++) {
            reversedArray[i] = arr[arr.length - i - 1];
        }
        
        // Print the reversed array
        System.out.print("reversedArray ");
        for (int j : reversedArray) {
            System.out.print(j + " ");
        }
    }

    // Main method to test the reverseArray method
    public static void main(String[] args) {
        // Initialize the original array
        int[] originalArray = {1, 2, 3, 4, 5};
        
        // Print the original array
        System.out.print("originalArray ");
        for (int i : originalArray) {
            System.out.print(i + " ");
        }
        
        // Call the reverseArray method to reverse and print the array
        reverseArray(originalArray);
    }
}

```
Time Complexity: O(n)

Copying elements to a new array is a linear operation.

Auxiliary Space Complexity: O(n)

Additional space is used to store the new array.

**Array Reverse Inbuilt Methods (Non In-place)**
```
class ReverseArray {
    public static void main(String[] args) {
        // Initialize the original array
        int[] arr = {1, 2, 3, 4, 5};
        
        // Create a new array to store the reversed elements, with the same length as the original array
        int[] revarr = new int[arr.length];
        
        // Loop through the original array and fill the reversed array
        for (int i = 0; i < arr.length; i++) {
            // Assign the element from the end of the original array to the current position in the reversed array
            revarr[i] = arr[arr.length - i - 1];
        }
        
        // Print the original array
        System.out.print("Original Array: ");
        for(int i : arr) {
            System.out.print(i + " ");
        }
        
        // Print the reversed array
        System.out.print("Reversed Array: ");
        for(int i : revarr) {
            System.out.print(i + " ");
        }
    }
}
```
Time Complexity: O(n) The reverse method typically has linear time complexity.

Auxiliary Space Complexity: O(n)

Additional space is used to store the reversed array.


**Array Reverse Using a Loop (In-place)**
```
class ReverseArray {
    // Method to reverse the contents of an array in place
    public static void ReverseArray(int[] arr) {
        int j = arr.length - 1; // Initialize j to the last index of the array
        int i = 0; // Initialize i to the first index of the array
        
        // Loop to swap elements until the middle of the array is reached
        while(i < j) {
            int temp = arr[j]; // Store the element at the end of the array in a temporary variable
            arr[j] = arr[i]; // Assign the element at the start of the array to the end
            arr[i] = temp; // Assign the temporary variable (originally the end element) to the start
            i++; // Move the start index forward
            j--; // Move the end index backward
        }
        
        // Print the reversed array
        System.out.print("Reversed Array: ");
        for(int k : arr) {
            System.out.print(k + " ");
        }
    }

    public static void main(String[] args) {
        int[] originalArray = {1, 2, 3, 4, 5}; // Initialize the array to be reversed
        
        // Print the original array
        System.out.print("Original Array: ");
        for(int i : originalArray) {
            System.out.print(i + " ");
        }
        
        // Call the method to reverse the array
        ReverseArray(originalArray);
    }
}

```
Time Complexity: O(n)

The loop runs through half of the array, so it’s linear with respect to the array size.

Auxiliary Space Complexity: O(1)

In-place reversal, meaning it doesn’t use additional space.


**Array Reverse Recursion (In-place or Non In-place)**
```
//Using Recursion
class ReverseArray{
    public static void reverseArray(int[] arr, int i, int j){
        if (i > j){
            return;
        }
            int temp = arr[j];
            arr[j] = arr[i];
            arr[i] = temp;
        
        reverseArray(arr, i + 1, j - 1);
    }
    public static void main(String[] args){
        int[] originalArray = {1,2,3,4,5};
        System.out.print("Original Array ");
        for(int i : originalArray){
            System.out.print(i);
        }
        reverseArray(originalArray, 0, originalArray.length - 1);
        System.out.print(" Reversed Array ");
        for(int k : originalArray){
            System.out.print(k);
        }
    }
}
```
Time Complexity: O(n). The recursion goes through each element once, so it’s linear.
Auxiliary Space Complexity: O(n) for non in-place, O(log n) for in-place (due to recursion stack).
```
Imagine a tree-like structure representing the recursive calls. Each level of the tree corresponds to a function call with its own stack frame. In the case of array reversal, as the recursion proceeds, the sub-array to be reversed gets smaller. This translates to fewer levels in the tree (lesser depth of recursion).

For example, consider an array of size 8. The maximum depth of recursion is 3 (log2(8) = 3). This means there will be at most 3 levels of function calls in the recursion tree, each level requiring a stack frame. This logarithmic relationship between the array size (n) and the depth of recursion (log n) leads to the O(log n) space complexity.

Here's a table summarizing the relationship between array size and recursion depth:

| Array Size (n) | Recursion Depth (log2(n)) |
|---|---|
| 2              | 1                       |
| 4              | 2                       |
| 8              | 3                       |
| 16             | 4                       |
| ...             | ...                      |

As you can see, the depth of recursion grows much slower than the array size itself.

Reasoning: As the recursion progresses, swapping elements from the beginning and end reduces the size of the sub-array to be reversed. This leads to fewer stack frames being created, resulting in a logarithmic relationship with the input size.

Why not O(n)?

The O(n) space complexity is more typical of non-in-place algorithms. In those cases, the algorithm typically creates a new data structure (like another array) to hold the reversed elements. This requires additional space proportional to the original input size (n).
```
**Array Reverse Stack (Non In-place)**
```
import java.util.Stack;

class ReverseArray {
    // Method to reverse the contents of an array using a stack
    public static void ReverseStack(int[] arr) {
        Stack<Integer> stack = new Stack<>(); // Create a stack to hold integer elements
        
        // Push all elements of the array onto the stack
        for(int i : arr) {
            stack.push(i);
        }
        
        // Pop elements from the stack back into the array, reversing their order
        for(int j = 0; j < arr.length; j++) {
            arr[j] = stack.pop();
        }
    }
    
    public static void main(String[] args) {
        int[] originalArray = {1, 2, 3, 4, 5}; // Initialize the array to be reversed
        
        // Print the original array
        System.out.print("Original Array ");
        for(int i : originalArray) {
            System.out.print(i + " ");
        }
        
        // Call the method to reverse the array
        ReverseStack(originalArray);
        
        // Print the reversed array
        System.out.print("Reversed Array ");
        for(int k : originalArray) {
            System.out.print(k + " ");
        }
    }
}
```
Time Complexity: O(n)

Pushing and popping each element onto/from the stack requires linear time.

Auxiliary Space Complexity: O(n)

Additional space is used to store the stack.
