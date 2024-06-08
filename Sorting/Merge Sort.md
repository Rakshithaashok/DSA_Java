**Merge Sort**

- Recursively divide array in 2, then sort, and then re-combine.
- run time complexity - O(n log n)
- space complexity = O(n)

```
public class MergeSort {
    public static void main(String[] args){
        int[] arr = {2,1,5,3,9,0,4,6};
        mergeSort(arr);
        for(int i : arr){
            System.out.print(i + " ");
        }
    }
    public static void mergeSort(int[] arr){
        if(arr.length <= 1)
            return;
        int mid = arr.length/2;
        int[] leftArray = new int[mid];
        int[] rightArray = new int[arr.length - mid];
        int i = 0;
        int j = 0;
        for (; i < arr.length; i++){
            if(i < mid){
                leftArray[i] = arr[i];
            }
            else{
                rightArray[j] = arr[i];
                j++;
            }
        }
        mergeSort(leftArray);
        mergeSort(rightArray);
        merge(leftArray, rightArray, arr);
    }

    public static void merge(int[] leftArray, int[]rightArray, int[] arr){
        int leftSize = arr.length/2;
        int rightSize = arr.length - leftSize;
        int i = 0, j = 0, k = 0;
        while ( i < leftSize && j < rightSize){
            if(leftArray[i] < rightArray[j]){
                arr[k] = leftArray[i];
                i++;
                k++;
            }
            else{
                arr[k] = rightArray[j];
                j++;
                k++;
            }
        }
        while(i < leftSize){
            arr[k] = leftArray[i];
            i++;
            k++;
        }
        while(j < rightSize){
            arr[k] = rightArray[j];
            j++;
            k++;
        }
    }
}

```
