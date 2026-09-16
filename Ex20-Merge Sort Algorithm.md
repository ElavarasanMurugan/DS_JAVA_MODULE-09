# Ex20 Sorting an Array using Merge Sort Algorithm
## DATE: 16-09-2026
## AIM:
To design a program that sorts a given array of integers in ascending order without using built-in sorting functions, achieving O(n log n) time complexity and minimal space usage.
## Algorithm
1. Start the program.
2. Define a `mergeSort()` method that recursively divides the array into two halves until each subarray contains a single element.
3. Define a `merge()` method to merge two sorted halves into a single sorted array.
4. In the `main()` method:

   * Initialize an integer array.
   * Display the original (unsorted) array.
   * Call the `mergeSort()` method to sort the array.
   * Display the sorted array.
5. Stop the program.
  

## Program:
```
/*
Program tosorts a given array of integers in ascending order without using built-in sorting functions
Developed by : Elavarasan M
RegisterNumber:  212224040083
*/
```

```java
import java.util.*;

public class Solution {
    
    private void swap(int[] arr, int index1, int index2) {
        int temp = arr[index1];
        arr[index1] = arr[index2];
        arr[index2] = temp;
    }

    private void heapify(int[] arr, int n, int i) {
        int largest = i;
        int left = 2 * i + 1;
        int right = 2 * i + 2;

        if (left < n && arr[left] > arr[largest]) {
            largest = left;
        }

        if (right < n && arr[right] > arr[largest]) {
            largest = right;
        }

        if (largest != i) {
            swap(arr, i, largest);
            heapify(arr, n, largest);
        }
    }

    private void heapSort(int[] arr) {
        int n = arr.length;
        for (int i = n / 2 - 1; i >= 0; i--) {
            heapify(arr, n, i);
        }

        for (int i = n - 1; i >= 0; i--) {
            swap(arr, 0, i);
            heapify(arr, i, 0);
        }
    }

    public int[] sortArray(int[] nums) {
        heapSort(nums);
        return nums;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Solution solution = new Solution();

        int n = sc.nextInt();
        
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }

        int[] sorted = solution.sortArray(nums);
        System.out.println("Sorted array:");
        System.out.println(Arrays.toString(sorted));

        sc.close();
    }
}
```
## Output:

![alt text](screenshots/image-5.png)

## Result:
The program has been successfully implemented and executed.
It sorts the given array of integers in ascending order using the Merge Sort algorithm with a time complexity of O(n log n) and minimal extra space.
