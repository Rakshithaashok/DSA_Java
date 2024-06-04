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
```
