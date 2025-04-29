# Ex13 Expression Tree
## DATE: 08.03.2025
## AIM:
To write a C function to construct an Expression Tree for the given Postfix Expression and display the output in the format of In-order ,Pre-order and Post-order traversal.

## Algorithm
1. Start with the root node.
2. If the tree is empty, create a new node as the root.
3. Else, compare the value to be inserted with the current node:
   - If it is smaller, recursively insert in the left subtree.
   - If it is greater, recursively insert in the right subtree.
4. Repeat until the correct position is found.
5. Insert the new node at that position.
 

## Program:
```
/*
Program to construct an Expression Tree for the given Postfix Expression and display the output in the format of In-order ,Pre-order and Post-order traversal.
Developed by: Thaksha Rishi
RegisterNumber:  212223100058
*/

#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>

// Define the structure of a tree node
struct Node {
    char data;
    struct Node* left;
    struct Node* right;
};

// Function to create a new node
struct Node* createNode(char value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

// Stack implementation for nodes
struct Node* stack[100];
int top = -1;

void push(struct Node* node) {
    stack[++top] = node;
}

struct Node* pop() {
    return stack[top--];
}

// Function to build expression tree
struct Node* buildExpressionTree(char postfix[]) {
    struct Node* temp;
    for (int i = 0; postfix[i] != '\0'; i++) {
        if (isalnum(postfix[i])) { // Operand
            temp = createNode(postfix[i]);
            push(temp);
        } else { // Operator
            temp = createNode(postfix[i]);
            temp->right = pop();
            temp->left = pop();
            push(temp);
        }
    }
    return pop();
}

// Inorder traversal
void inorder(struct Node* root) {
    if (root != NULL) {
        inorder(root->left);
        printf("%c ", root->data);
        inorder(root->right);
    }
}

// Preorder traversal
void preorder(struct Node* root) {
    if (root != NULL) {
        printf("%c ", root->data);
        preorder(root->left);
        preorder(root->right);
    }
}

// Postorder traversal
void postorder(struct Node* root) {
    if (root != NULL) {
        postorder(root->left);
        postorder(root->right);
        printf("%c ", root->data);
    }
}

int main() {
    char postfix[100];
    printf("Enter the postfix expression: ");
    scanf("%s", postfix);

    struct Node* root = buildExpressionTree(postfix);

    printf("\nIn-order Traversal: ");
    inorder(root);

    printf("\nPre-order Traversal: ");
    preorder(root);

    printf("\nPost-order Traversal: ");
    postorder(root);

    return 0;
}

```

## Output:

![image](https://github.com/user-attachments/assets/b63967f6-fee0-4cea-bb67-d3c1f48dcbfa)


## Result:
Thus, the C program to display the Expression Tree in the format of In-order ,Pre-order and Post-order traversal.
