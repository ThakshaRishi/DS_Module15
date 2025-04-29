# Ex11 Tree Representation and Traversal
## DATE: 04.03.2025
## AIM:
To write a C function to perform post order traversal of a binary tree.

## Algorithm

1. Start from the root node.

2. Recursively traverse the left subtree.

3. Recursively traverse the right subtree.

4. Visit (process/print) the root node.

5. Repeat the above steps until all nodes are visited.  

## Program:
```
/*
Program to perform post order traversal of a binary tree.
Developed by: Thaksha Rishi
RegisterNumber: 212223100058
*/

#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

struct Node* createNode(int value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

void postOrderTraversal(struct Node* root) {
    if (root == NULL)
        return;
    
    postOrderTraversal(root->left);    
    postOrderTraversal(root->right);   
    printf("%d ", root->data);         
}

int main() {
    struct Node* root = createNode(1);
    root->left = createNode(2);
    root->right = createNode(3);
    root->left->left = createNode(4);
    root->left->right = createNode(5);

    printf("Postorder traversal of the binary tree:\n");
    postOrderTraversal(root);

    return 0;
}

```

## Output:

![image](https://github.com/user-attachments/assets/7bf72162-745c-492d-8f5f-fec07919adde)


## Result:
Thus, the function to perform post order traversal of a binary tree is implemented successfully
