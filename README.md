# begining
its my second repository 
class MergeSort {

    // Merge Sort function
    void mergeSort(int[] arr, int l, int h) {
        if (l < h) {
            int m = (l + h) / 2;
            mergeSort(arr, l, m);
            mergeSort(arr, m + 1, h);
            merge(arr, l, m, h);
        }
    }

    // Merge function
    void merge(int[] arr, int l, int m, int h) {
        // Find sizes of two subarrays to be merged
        int n1 = m - l + 1;
        int n2 = h - m;

        // Create temporary arrays
        int[] L = new int[n1];
        int[] R = new int[n2];

        // Copy data to temp arrays
        for (int i = 0; i < n1; ++i)
            L[i] = arr[l + i];
        for (int j = 0; j < n2; ++j)
            R[j] = arr[m + 1 + j];

        // Merge the temp arrays
        int i = 0, j = 0;
        int k = l;
        while (i < n1 && j < n2) {
            if (L[i] <= R[j]) {
                arr[k] = L[i];
                i++;
            } else {
                arr[k] = R[j];
                j++;
            }
            k++;
        }

        // Copy remaining elements of L[] if any
        while (i < n1) {
            arr[k] = L[i];
            i++;
            k++;
        }

        // Copy remaining elements of R[] if any
        while (j < n2) {
            arr[k] = R[j];
            j++;
            k++;
        }
    }

    // Utility function to print an array
    void printArray(int[] arr) {
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();
    }

    // Main function
    public static void main(String[] args) {
        MergeSort sorter = new MergeSort();
        int[] arr = {12, 11, 13, 5, 6, 7};
        System.out.println("Given Array:");
        sorter.printArray(arr);

        sorter.mergeSort(arr, 0, arr.length - 1);

        System.out.println("Sorted Array:");
        sorter.printArray(arr);
    }
}
