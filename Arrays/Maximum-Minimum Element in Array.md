**Using Max Min Methods**

```
class MaxMinArray {
    public static int MaxElement(int[] arr){
        int max = Integer.MIN_VALUE;
        for(int i = 0; i < arr.length; i++){
            if(arr[i] > max){
                max = arr[i];
            }
        }
        return max;
    }
    public static int MinElement(int[] arr){
        int min = Integer.MAX_VALUE;
        for(int i = 0; i < arr.length; i++){
            if(arr[i] < min){
                min = arr[i];
            }
        }
        return min;
    }
    public static void main(String[] args){
        int[] arr = {4,5,6, 24, 7, 11};
        System.out.println("Max element in Array : " + MaxElement(arr));
        System.out.println("Min element in Array : " + MinElement(arr));
    }
}
```
Time Complexity: O(N)

Auxiliary Space: O(1)

**Using Arrays.sort() method**
```
Package Name	Description
java.io 	Input/Output Operations (Files, Streams)
java.util	Utility Classes and Interfaces (Collections, Iterators, Arrays, Date/Time, etc.)
```

```
import java.util.*;

class MaxMinArray {
    public static void main (String[] args){
        int[] arr = {4,1, 24, 6, 32, -10};
        Arrays.sort(arr);
        System.out.println("Max Element " + arr[0]);
        System.out.println("Min Element " + arr[arr.length - 1]);
    }
}
```
Time complexity: O(n log n), where n is the number of elements in the array, as we are using a sorting algorithm.

Auxilary Space: is O(1), as we are not using any extra space.

**Maximum and minimum of an array using Linear search**
```
class MinMaxArray {

  // This class defines methods to find the minimum and maximum elements in an array.

  public static void minmax(int[] arr) {
    // This method takes an integer array 'arr' as input and finds the minimum and maximum values.

    int min, max;
    // Declare integer variables 'min' and 'max' to store the minimum and maximum values, respectively.

    if (arr.length == 1) {
      // If the array has only one element, both min and max are that element.
      System.out.println("min: " + arr[0]);
      System.out.println("max: " + arr[0]);
      return; // Early exit if there's only one element
    }

    // Handle the first two elements separately to ensure correct initialization
    if (arr[0] < arr[1]) {
      min = arr[0];
      max = arr[1];
    } else {
      max = arr[0];
      min = arr[1];
    }

    for (int i = 2; i < arr.length; i++) {
      // Iterate through the array starting from the third element (since first two are handled)
      if (arr[i] < min) {
        min = arr[i]; // Update minimum if current element is smaller
      } else if (arr[i] > max) {
        max = arr[i]; // Update maximum if current element is larger
      }
    }

    System.out.println("Max: " + max);
    System.out.println("Min: " + min);
  }

  public static void main(String[] args) {
    int[] arr = {1, 52, 45, 32, 24, 7, 82, -2};
    minmax(arr); // Call the minmax method to find minimum and maximum elements
  }
}

Time Complexity: O(n)

Auxiliary Space: O(1) as no extra space was needed.

```
**Maximum and minimum of an array using the Tournament Method (divide array into two)**
```
import java.util.*; // Import for functionalities like Math.min and Math.max

class MinMax {

  // This class defines a method to find the minimum and maximum elements in an array.

  public static int[] minmax(int[] arr, int low, int high) {
    // This method takes an integer array 'arr', the starting index 'low', and the ending index 'high' as input.
    // It returns an array containing the minimum and maximum values found in the specified sub-array.

    int min = Integer.MAX_VALUE; // Initialize min to maximum integer value (for comparison)
    int max = Integer.MIN_VALUE; // Initialize max to minimum integer value (for comparison)

    // Base cases for handling arrays with one or two elements
    if (low == high) {
      // If there's only one element, both min and max are that element
      min = arr[low];
      max = arr[low];
      return new int[]{min, max}; // Return an array containing min and max
    }

    if (low + 1 == high) {
      // If there are two elements, compare them to find min and max
      min = Math.min(arr[low], arr[high]); // Use Math.min for cleaner comparison
      max = Math.max(arr[low], arr[high]); // Use Math.max for cleaner comparison
      return new int[]{min, max}; // Return an array containing min and max
    }

    // Recursive case for arrays with more than two elements
    int mid = (low + high) / 2; // Find the middle index for dividing the array

    // Recursively find min and max in the left half (low to mid)
    int[] mml = minmax(arr, low, mid);

    // Recursively find min and max in the right half (mid+1 to high)
    int[] mmr = minmax(arr, mid + 1, high);

    // Update min and max based on comparisons between halves
    min = Math.min(mml[0], mmr[0]); // Find the overall minimum
    max = Math.max(mml[1], mmr[1]); // Find the overall maximum

    // Return an array containing the minimum and maximum values found
    return new int[]{min, max};
  }

  public static void main(String[] args) {
    int[] arr = {5, 3, 2, 6, 7, 24, -245};
    int[] getminmax = minmax(arr, 0, arr.length - 1); // Call minmax for the entire array
    System.out.println("Minimum element: " + getminmax[0]);
    System.out.println("Maximum element: " + getminmax[1]);
  }
}
```

**without Math.min and Math.max function in tournament method**
```
import java.util.*; // Import for functionalities like finding array length

class MinMax {

  // This class defines a method to find the minimum and maximum elements in an array.

  public static int[] minmax(int[] arr, int low, int high) {
    // This method takes an integer array 'arr', the starting index 'low', and the ending index 'high' as input.
    // It returns an array containing the minimum and maximum values found in the specified sub-array.

    int min = Integer.MAX_VALUE; // Initialize min to maximum integer value (for comparison)
    int max = Integer.MIN_VALUE; // Initialize max to minimum integer value (for comparison)

    // Base cases for handling arrays with one or two elements
    if (low == high) {
      // If there's only one element, both min and max are that element
      min = arr[low];
      max = arr[low];
      return new int[]{min, max}; // Return an array containing min and max
    }

    if (low + 1 == high) {
      // If there are two elements, compare them to find min and max
      if (arr[low] < arr[high]) {
        min = arr[low];
        max = arr[high];
      } else {
        min = arr[high];
        max = arr[low];
      }
      return new int[]{min, max}; // Return an array containing min and max
    }

    // Recursive case for arrays with more than two elements
    int mid = (low + high) / 2; // Find the middle index for dividing the array

    // Recursively find min and max in the left half (low to mid)
    int[] mml = minmax(arr, low, mid);

    // Recursively find min and max in the right half (mid+1 to high)
    int[] mmr = minmax(arr, mid + 1, high);

    // Update min and max based on comparisons between halves
    min = (mml[0] < mmr[0]) ? mml[0] : mmr[0];  // Use ternary operator for min
    // Check if element at index 0 in mml is less than element at index 0 in mmr. If true, assign mml[0] to min, otherwise assign mmr[0]
    max = (mml[1] > mmr[1]) ? mml[1] : mmr[1];  // Use ternary operator for max
    // Check if element at index 1 in mml is greater than element at index 1 in mmr. If true, assign mml[1] to max, otherwise assign mmr[1]

    // Return an array containing the minimum and maximum values found
    return new int[]{min, max};
  }

  public static void main(String[] args) {
    int[] arr = {5, 3, 2, 6, 7, 24, -245};
    int[] getminmax = minmax(arr, 0, arr.length - 1); // Call minmax for the entire array (0 to length-1)
    System.out.println("Minimum element: " + getminmax[0]);
    System.out.println("Maximum element: " + getminmax[1]);
  }
}
```
Time Complexity: O(n)

Auxiliary Space: O(log n) as the stack space will be filled for the maximum height of the tree formed during recursive calls same as a binary tree.
