**Selection Sort**
- Search through an array and keep track of the minimum value during each iteration.
- At the end of each iteration, we swap variables
- Quadratic time O(n^2)
- small data set - okay
- large data set - bad


```
class SelectionSort {

  // This class implements the Selection Sort algorithm.
  public static void SelectionSort(int[] arr) {
    // Outer loop iterates through the array from the beginning to the second last element.
    for (int i = 0; i < arr.length - 1; i++) {
      // Initialize the 'min' index as the current index 'i'.
      // This assumes the element at 'i' is the minimum for now.
      int min = i;

      // Inner loop iterates through the unsorted part of the array (elements after 'i').
      for (int j = i + 1; j < arr.length; j++) {
        // Check if the element at 'j' is less than the current minimum element.
        if (arr[min] > arr[j]) {
          // If a smaller element is found, update the 'min' index to 'j'.
          min = j;
        }
      }

      // After the inner loop, 'min' holds the index of the minimum element in the unsorted part.
      // Swap the element at the current index 'i' with the element at the 'min' index.
      int temp = arr[i];
      arr[i] = arr[min];
      arr[min] = temp;
    }
  }

  // Example usage
  public static void main(String[] args) {
    int[] arr = {4, 24, 1, 6, -1, 21, 29, 100, 8, 9};
    SelectionSort(arr);
    System.out.print("Sorted array: ");
    for (int i : arr) {
      System.out.print(i + " ");
    }
  }
}
```
