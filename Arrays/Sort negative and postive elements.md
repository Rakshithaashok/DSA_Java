**Move all negative numbers to beginning and positive to end with constant extra space**

Examples : 

Input: -12, 11, -13, -5, 6, -7, 5, -3, -6

Output: -12 -13 -5 -7 -3 -6 11 6 5

**Approach 1:**
The idea is to simply apply the partition process of quicksort. 
```
class Sort {
    // Method to sort the array such that all negative numbers are moved to the beginning
    public static void sort(int[] arr) {
        int j = 0;  // Initialize a pointer j to keep track of the position for swapping

        // Traverse the array
        for(int i = 0; i < arr.length; i++) {
            // Check if the current element is negative
            if(arr[i] < 0) {
                // If the current element is negative and i is not equal to j, swap arr[i] and arr[j]
                if(i != j) {
                    int temp = arr[i];  // Store the current element in a temporary variable
                    arr[i] = arr[j];    // Move the element at index j to the current index i
                    arr[j] = temp;      // Assign the temporary variable (original arr[i]) to index j
                }
                j++;  // Increment the pointer j
            }
        }
    }

    public static void main(String[] args) {
        // Define an array with a mix of negative and positive numbers
        int[] arr = {-2, 5, -5, -10, 15, 24, -8, 0};

        // Call the sort method to rearrange the array
        sort(arr);

        // Print the sorted array
        for(int i : arr) {
            System.out.print(i + " ");  // Print each element of the array followed by a space
        }
    }
}
```
Time complexity: O(N) 

Auxiliary Space: O(1)

**Two Pointer Approach:** The idea is to solve this problem with constant space and linear time is by using a two-pointer or two-variable approach where we simply take two variables like left and right which hold the 0 and N-1 indexes. Just need to check that :

- Check If the left and right pointer elements are negative then simply increment the left pointer.
- Otherwise, if the left element is positive and the right element is negative then simply swap the elements, and simultaneously increment and decrement the left and right pointers.
- Else if the left element is positive and the right element is also positive then simply decrement the right pointer.
- Repeat the above 3 steps until the left pointer ? right pointer.

```
class Sort {
    // Method to sort the array such that all negative numbers are moved to the beginning
    public static void sort(int[] arr) {
        int i = 0;  // Initialize pointer i to start of the array
        int j = arr.length - 1;  // Initialize pointer j to end of the array

        // Loop until the two pointers cross each other
        while (i < j) {
            // If both elements at pointers i and j are negative, move the i pointer to the right
            if (arr[i] < 0 && arr[j] < 0) {
                i++;
            }
            // If the element at i is non-negative and the element at j is negative, swap them
            if (arr[i] >= 0 && arr[j] < 0) {
                int temp = arr[j];  // Store the element at j in a temporary variable
                arr[j] = arr[i];    // Move the element at i to position j
                arr[i] = temp;      // Assign the temporary variable (original arr[j]) to position i
                i++;  // Move pointer i to the right
                j--;  // Move pointer j to the left
            }
            // If both elements at pointers i and j are non-negative, move the j pointer to the left
            if (arr[i] >= 0 && arr[j] >= 0) {
                j--;
            }
        }
    }

    public static void main(String[] args) {
        // Define an array with a mix of negative and positive numbers
        int[] arr = {10, -2, 24, 5, 0, -4, -10};

        // Call the sort method to rearrange the array
        sort(arr);

        // Print the sorted array
        for (int i : arr) {
            System.out.print(i + " ");  // Print each element of the array followed by a space
        }
    }
}

```

Time Complexity: O(N)

Auxiliary Space: O(1)

**Approach 3:**

```
class Sort {
    // Method to sort the array such that all negative numbers are moved to the beginning
    public static void sort(int[] arr) {
        int i = 0;  // Initialize pointer i to start of the array
        int j = arr.length - 1;  // Initialize pointer j to end of the array

        // Loop until the two pointers cross
        while (i < j) {
            // If the element at i is negative, move the i pointer to the right
            if (arr[i] < 0) {
                i++;
            }
            // If the element at i is non-negative
            else {
                // Swap the elements at i and j
                int temp = arr[i];  // Store the element at i in a temporary variable
                arr[i] = arr[j];    // Move the element at j to position i
                arr[j] = temp;      // Assign the temporary variable (original arr[i]) to position j
                j--;  // Move pointer j to the left
            }
        }
    }

    public static void main(String[] args) {
        // Define an array with a mix of negative and positive numbers
        int[] arr = {10, -2, 24, 5, 0, -4, -10, -10, -20, 0};

        // Call the sort method to rearrange the array
        sort(arr);

        // Print the sorted array
        for (int i : arr) {
            System.out.print(i + " ");  // Print each element of the array followed by a space
        }
    }
}
```
Time complexity: O(N) 

Auxiliary Space: O(1)

**Approach 4: Two-Pass Approach**
Another approach to move all negative numbers to the beginning and positive numbers to the end of an array with constant extra space is to use a two-pass approach, where we first count the number of negative elements, and then rearrange the elements accordingly.

Steps:
Follow the given steps to solve the problem:

Initialize a variable negCount to count the number of negative elements.
Traverse the array to count the number of negative elements.
Initialize two pointers i and j where i starts from 0 and j starts from negCount.
Iterate through the array using i and j pointers until i is less than negCount and j is less than n.
If the element at index i is negative, increment i.
If the element at index j is non-negative, increment j.
If the element at index i is negative and the element at index j is non-negative, swap the elements at indices i and j.
Increment both i and j.

```
class Sort {
    // Method to sort the array such that all negative numbers are moved to the beginning
    public static void sort(int[] arr) {
        int negcount = 0;  // Initialize counter for negative numbers
        
        // First pass to count the number of negative numbers in the array
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] < 0) {
                negcount++;
            }
        }

        int j = 0;  // Pointer to iterate over the part of the array with negative numbers
        int k = negcount;  // Pointer to iterate over the part of the array with non-negative numbers

        // Second pass to rearrange the array such that all negative numbers are at the beginning
        while (j < negcount && k < arr.length) {
            if (arr[j] < 0) {
                j++;  // Move the pointer j to the right if the current element is negative
            } else if (arr[k] >= 0) {
                k++;  // Move the pointer k to the right if the current element is non-negative
            } else {
                // Swap the elements at indices j and k
                int temp = arr[j];  // Store the element at j in a temporary variable
                arr[j] = arr[k];    // Move the element at k to position j
                arr[k] = temp;      // Assign the temporary variable (original arr[j]) to position k
                j++;  // Move pointer j to the right
                k++;  // Move pointer k to the right
            }
        }
    }

    public static void main(String[] args) {
        // Define an array with a mix of negative and positive numbers
        int[] arr = {10, -2, 24, 5, 0, -4};

        // Call the sort method to rearrange the array
        sort(arr);

        // Print the sorted array
        for (int i : arr) {
            System.out.print(i + " ");  // Print each element of the array followed by a space
        }
    }
}
```
Time complexity: O(N)

Auxiliary Space: O(1)
