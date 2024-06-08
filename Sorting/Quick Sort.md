**Quick Sort** 
Youtube - [https://youtu.be/Vtckgz38QHs?si=zLZ5oZ_s-Sc85NJE]

- moves smaller elements to left of pivot.
- recursively divide array in 2 partitions
- run time -> best case O(n log(n))
           -> average case O(n log(n))
           -> worst case O(n^2) (if already sorted)
  - space complexity = O(log(n)) due to recursion
 
    ```
    public class QuickSort {
    public static void main(String[] args){
        int[] arr = {2,5,6,1,4,3,0,8,7,9};
        quicksort(arr, 0, arr.length - 1);
        for(int i : arr){
            System.out.print(i + " ");
        }
    }

    public static void quicksort(int[] arr, int start, int end){
        if (end <= start)
            return;
        int pivot = partition(arr, start, end);
        quicksort(arr, start, pivot-1);
        quicksort(arr, pivot+1, end);
    }

    public static int partition(int[] arr, int start, int end){
        int pivot = arr[end];
        int j = 0;
        int i = j - 1;
        for(; j <= end - 1; j++){
            if (arr[j] < pivot){
                i++;
                int temp = arr[j];
                arr[j] = arr[i];
                arr[i] = temp;
            }
        }
        i++;
        int temp = arr[end];
        arr[end] = arr[i];
        arr[i] = temp;

        return i;
    }
}

    ```
