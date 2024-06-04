**Insertion Sort** [https://youtu.be/8mJ-OhcfpYg?si=bC_tGHJwulO_41sc]
- After comparing elements to the left,
- Shift elements to the right to make room to insert a value,
- Quadratic time 0(n^2)
- small data set - decent
- large data set - BAD
- less steps compared to bubble sort
- Best case is 0(n) compared to Selection sort 0(n^2)


```
class InsertionSort {

  // This class implements the Insertion Sort algorithm.
  public static void InsertionSort(int[] arr) {
    // Loop through the array from the second element (index 1) to the end.
    for (int i = 1; i < arr.length; i++) {
      // Store the current element (to be inserted) in a temporary variable.
      int temp = arr[i];
      // Initialize an index variable 'j' to compare with the element before the current element.
      int j = i - 1;

      // Loop while j is within the array bounds (not less than 0) and the element at j is greater than the temporary element (to be inserted).
      while (j >= 0 && arr[j] > temp) {
        // Shift the larger element one position ahead to create a space for the current element (temp).
        arr[j + 1] = arr[j];
        // Decrement j to compare with the previous element.
        j--;
      }

      // Insert the current element (temp) at the correct position (j + 1).
      arr[j + 1] = temp;
    }
  }

  // Example usage
  public static void main(String[] args) {
    int[] arr = {4, 24, 1, 6, -1, 21, 29, 100, 8, 9};
    InsertionSort(arr);
    System.out.print("Sorted array: ");
    for (int i : arr) {
      System.out.print(i + " ");
    }
  }
}
```
