**Bubble Sort** [https://youtu.be/Dv4qLJcxus8?si=lecNACeb1ojLuBh6]
- pairs of adjacent elements are compared, and the elements are swapped if they are not in order
- Quadratic time O(n^2)
- small data set - okay-ish
- large data set - BAD (NOT Recommended)


```
class BubbleSort{
    // Static method to perform bubble sort on an array of integers
    public static void bubblesort(int[] arr){
        // Outer loop iterates over each element in the array
        for(int i = 0; i < arr.length - 1; i++){
            // Inner loop performs the comparison and swapping of adjacent elements
            for(int j = 0; j < arr.length - i - 1; j++){
                // If the current element is greater than the next element, swap them
                if(arr[j] > arr[j+1]){
                    // Swap the elements
                    int temp = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                }
            }
        }
    }

    // Main method to test the bubble sort algorithm
    public static void main(String[] args){
        // Initialize an array of integers
        int[] arr = {4, 24, 1, 6, -1, 21, 29, 100, 8, 9};
        // Call the bubblesort method to sort the array
        bubblesort(arr);
        // Print the sorted array
        for(int i : arr){
            System.out.print(i + " ");
        }
    }
}

```


