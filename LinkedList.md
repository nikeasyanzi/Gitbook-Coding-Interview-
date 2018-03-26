# 4.Linked List

22 Merge Two Sorted Lists

23 Add Two Numbers
https://leetcode.com/problems/add-two-numbers/description/

```c
int addNode(int val, int carryin)
{
    struct ListNode* curr=head;
    struct ListNode* newnode=malloc(sizeof(struct ListNode));
    newnode->next=NULL;
    int carryout=0;
    if(val+carryin<10)
    {
        newnode->val=val+carryin;
        carryout=0;
    }
    else
    {
        //printf(" in add nodeval=%d carryin=%d,",val, carryin);
        newnode->val=val+carryin-10;
        carryout=1;
    }
    if(curr==NULL)
    {
        head=newnode;
    }
    else
    {
        while(curr->next!=NULL)
        {
            curr=curr->next;
        }
        curr->next=newnode;
    }
    //printf(" in addnode currl1->val=%d carryout=%d\n", newnode->val,carryout);
    return carryout;
}

struct ListNode* addTwoNumbers(struct ListNode* l1, struct ListNode* l2)
{
    struct ListNode* currl1=l1;
    struct ListNode* currl2=l2;
    int carryin=0;
    int carryout;
    int l2val=0;
    int l1val=0;
    while(currl1!=NULL|| currl2!=NULL||carryin!=0)
    {
        l2val=0;
        l1val=0;

        if(currl1!=NULL)
        {
            l1val=currl1->val;
            currl1=currl1->next;
        }
        if(currl2!=NULL)
        {
            l2val=currl2->val;
            currl2=currl2->next;
        }
        carryout=addNode(l1val+l2val,carryin);
        carryin=carryout;
    }
    return head;
}
```
這題要考慮 

1.有進位的問題 
2.list 長短不一致的問題

原本addTwoNumbers是寫成


```c

struct ListNode* addTwoNumbers(struct ListNode* l1, struct ListNode* l2)
{
    struct ListNode* currl1=l1;
    struct ListNode* currl2=l2;
    int carryin=0;
    int carryout;
    while(currl1!=NULL|| currl2!=NULL||carryin!=0){
        if(currl1==NULL && currl2!=NULL){
            ...
        }
        if(currl2==NULL&& currl1!=NULL){
            ...
        }
        if(currl1!=NULL&& currl2!=NULL){
            ... //move currl1 and currl2 points to the next one
        }

        if(currl1==NULL&& currl2==NULL){
            ... //now both curr1 and curr2 are null, 
                //the program runs into a bug without reset carryin
        }
        carryin=carryout;
    }
    return head;
}
```

```c

struct ListNode* addTwoNumbers(struct ListNode* l1, struct ListNode* l2)
{
    struct ListNode* currl1=l1;
    struct ListNode* currl2=l2;
    int carryin=0;
    int carryout;
    while(currl1!=NULL|| currl2!=NULL||carryin!=0){
        if(currl1==NULL && currl2!=NULL){
                ...
        }
        else{
            if(currl2==NULL&& currl1!=NULL){
                ...
            }
            else{
                if(currl1!=NULL&& currl2!=NULL){
                     ...
                }
                else{
                    if(currl1==NULL&& currl2==NULL){
                         ...
                    }
                }
            }
        }
        carryin=carryout;
    }
    return head;
}
```
但其實這兩種  寫法  太直覺  但 if-else 太複雜  

尤其第一種會有bug  (一度卡很久)

這題還有小bug 懶得修


24 Swap Nodes in Pairs

25 Merge K Sorted Linked Lists

26 Copy List with Random Pointer



Misc:
## Reverse a linked list
```c
static void reverse(struct Node** head_ref)
{
    struct Node* prev   = NULL;
    struct Node* current = *head_ref;
    struct Node* next = NULL;
    while (current != NULL)
    {
        next  = current->next;  
        current->next = prev;   
        prev = current;
        current = next;
    }
    *head_ref = prev;
}
```
https://www.geeksforgeeks.org/reverse-a-linked-list/
## Tortoise and Hare
```c




```

loop detection
http://codingfreak.blogspot.com/2012/09/detecting-loop-in-singly-linked-list_22.html

find loop entry
http://codingfreak.blogspot.com/2012/12/detecting-first-node-in-a-loop.html
這個find loop entry ion完馬上找
