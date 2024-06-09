[https://www.geeksforgeeks.org/rearrange-array-alternating-positive-negative-items-o1-extra-space/]

**Rearrange array in alternating positive & negative items with O(1) extra space**

```
public class RearrangeArray {
    public static void main(String[] args){
        int[] arr = {-5, -2, 5, 2, 4, 7, 1, 8, 0, -8 };
        System.out.println("Initial Array");
        printarr(arr);
        rearrange(arr);
        System.out.println("Rearranged Array");
        printarr(arr);
    }
    public static void printarr(int[] arr){
        for(int i : arr){
            System.out.print(i + " ");
        }
        System.out.println();
    }
    public static void rearrange(int[] arr){
        int check = -1;
        for(int index = 0; index < arr.length; index++){
            if(check >= 0) {
                if ((arr[index] >= 0 && arr[check] < 0) || (arr[index] < 0 && arr[check] >= 0)) {
                    rightrotate(arr, check, index);

                    if (index - check >= 2) {
                        check = check + 2;
                    } else {
                        check = -1;
                    }
                }
            }
            if(check == -1) {
                if ((arr[index] < 0 && (index & 0x01) == 1) || (arr[index] >= 0 && (index & 0x01) == 0)) {
                    check = index;
                }
            }
        }
    }
    public static void rightrotate(int[] arr, int check, int index){
        int temp = arr[index];
        for(int curr = index - 1; curr > check; curr--){
            arr[curr + 1] = arr[curr];
        }
        arr[check] = temp;
    }
}

```
