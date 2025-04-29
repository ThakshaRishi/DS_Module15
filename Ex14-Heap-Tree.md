# Ex14 Heap Tree
## DATE:07.03.2025
## AIM:
To write a C function to delete an element in a Heap Tree.

## Algorithm
1. Find the element to be deleted: Search for the element in the heap.

2. Replace the element with the last element: Replace the element to be deleted with the last element in the heap.

3. Reduce the size of the heap: Decrease the heap size by 1 to exclude the last element.

4. Heapify: Restore the heap property by heapifying the tree starting from the index of the replaced element.

5. Handle heap property violations: Ensure that after heapifying, the heap remains either a max-heap or a min-heap.
## Program:
```
/*
Program to delete an element in a Heap Tree
Developed by: Thaksha Rishi
RegisterNumber: 212223100058
*/
#include <stdio.h>

#define MAX_SIZE 100

// Function to swap two elements
void swap(int *x, int *y) {
    int temp = *x;
    *x = *y;
    *y = temp;
}

// Function to heapify a subtree rooted with index i
void heapify(int arr[], int n, int i) {
    int largest = i; // Initialize largest as root
    int left = 2 * i + 1; // left = 2*i + 1
    int right = 2 * i + 2; // right = 2*i + 2

    // If left child is larger than root
    if (left < n && arr[left] > arr[largest]) {
        largest = left;
    }

    // If right child is larger than largest so far
    if (right < n && arr[right] > arr[largest]) {
        largest = right;
    }

    // If largest is not root
    if (largest != i) {
        swap(&arr[i], &arr[largest]);
        // Recursively heapify the affected sub-tree
        heapify(arr, n, largest);
    }
}

// Function to delete an element from the heap
void deleteHeapNode(int arr[], int *n, int key) {
    int i;

    // Find the index of the element to be deleted
    for (i = 0; i < *n; i++) {
        if (arr[i] == key) {
            break;
        }
    }

    // If the element is not found
    if (i == *n) {
        printf("Element not found in the heap.\n");
        return;
    }

    // Replace the element with the last element
    arr[i] = arr[*n - 1];
    (*n)--;

    // Heapify the root node to maintain the heap property
    heapify(arr, *n, i);
}

// Function to print the heap
void printHeap(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int heap[] = {10, 20, 15, 30, 40, 50, 100, 25, 45};
    int n = sizeof(heap) / sizeof(heap[0]);
    int key;

    printf("Original Heap:\n");
    printHeap(heap, n);

    printf("Enter the element to delete: ");
    scanf("%d", &key);

    deleteHeapNode(heap, &n, key);

    printf("Heap after deletion:\n");
    printHeap(heap, n);

    return 0;
}

```

## Output:

![image](https://github.com/user-attachments/assets/13da3ecc-c5a3-459b-bc7d-2d9335beac91)


## Result:
Thus, the function to delete an element in a Heap Tree is implemented successfully.
