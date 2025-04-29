# Ex15 Largest Element in BST
## DATE: 12.03.2025
## AIM:
To Write a c program to find the largest value in a Binary Search Tree.

## Algorithm
1. Start from the root: Begin from the root node of the BST.

2. Traverse right: In a BST, the largest element is always located at the rightmost node.

3. Iterate until the rightmost node: Keep moving to the right child node until a node does not have a right child.

4. Return the rightmost node: The node that doesn’t have a right child will contain the largest value in the tree. 

## Program:
```
/*
Program to find and display the priority of the operator in the given Postfix expression
Developed by: Thaksha Rishi
RegisterNumber:  212223100058
*/
#include <stdio.h>
#include <stdlib.h>

// Define structure for a node
struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

// Function to create a new node
struct Node* newNode(int data) {
    struct Node* node = (struct Node*)malloc(sizeof(struct Node));
    node->data = data;
    node->left = node->right = NULL;
    return node;
}

// Function to find the largest element in a BST
int findLargest(struct Node* root) {
    if (root == NULL) {
        return -1; // Return -1 if tree is empty
    }
    // Traverse to the rightmost node
    while (root->right != NULL) {
        root = root->right;
    }
    return root->data; // Return the data of the rightmost node
}

int main() {
    // Create a sample BST
    struct Node* root = newNode(50);
    root->left = newNode(30);
    root->right = newNode(70);
    root->left->left = newNode(20);
    root->left->right = newNode(40);
    root->right->left = newNode(60);
    root->right->right = newNode(80);

    // Find and display the largest value in the BST
    int largest = findLargest(root);
    if (largest != -1) {
        printf("The largest value in the BST is: %d\n", largest);
    } else {
        printf("The BST is empty.\n");
    }

    return 0;
}

```

## Output:

![image](https://github.com/user-attachments/assets/1e81b6ad-7fbd-4ba3-ba0a-8445c23ccc31)


## Result:
Thus, the C program to find the largest value in a Binary Search Tree is implemented successfully.
