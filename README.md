# Tree-DS-implementation-
#include <stdio.h>
#include<conio.h>
struct node
{
    int data;
    struct node *left, *right;
};
struct node * create()
{
    int x;
    struct node *newnode=0;
    newnode=(struct node *)malloc(sizeof(struct node *));
    printf("Enter data in your tree, press -1 if you do not wish to enter any data: \n");
    scanf("%d",&x);
    if(x==-1)
    {
        return 0;
    }
    else
    {
        newnode->data=x;
        printf("Enter data into the left child node----\n ");
        newnode->left=create();
        printf("Enter data into the right child node----\n ");
        newnode->right=create();
        return newnode;
    }
};

void preorder(struct node *root)
{
    //the preorder traversal of a tree follows Root->Left->Right approach.
    if(root==0)
    {
        return;
    }
    else
    {
        printf("%d \t",root->data);
        preorder(root->left);
        preorder(root->right);
    }
};

void postorder(struct node *root)
{
    //The postorder traversal of a tree, follows Left->Right->Root approach.
    if(root==0)
    {
        return;
    }
    else
    {
        postorder(root->left);
        postorder(root->right);
        printf("%d \t",root->data);
    }
};
void inorder(struct node *root)
{
    //the inorder traversal of a tree follows Left->Root->Right approach.
    if(root==0)
    {
        return;
    }
    else
    {
        inorder(root->left);
        printf("%d\t",root->data);
        inorder(root->right);
    }
};

void main()
{
    struct node *root;
    root=0;
    root=create();
    int ch;
    int choice;
    do
    {
        printf("Enter your choice: 1.Preorder traversal  2.Postorder traversal  3.Inorder Traversal \n");
        scanf("%d",&choice);
        switch(choice)
        {
        case 1:
            {
                preorder(root);
                break;
            }
        case 2:
            {
                postorder(root);
                break;
            }
        case 3:
            {
                inorder(root);
                break;
            }
        default:
            printf("Wrong choice!\n");
        }
        printf("do you wish to continue? (1/0) \n");
        scanf("%d",ch);
    }while(ch==1);
    
    getch();
}
