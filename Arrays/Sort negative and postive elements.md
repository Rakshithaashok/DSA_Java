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
