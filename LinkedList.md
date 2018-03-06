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


這題原本是寫成
'''
struct ListNode* addTwoNumbers(struct ListNode* l1, struct ListNode* l2)
{

struct ListNode* currl1=l1;
struct ListNode* currl2=l2;
int carryin=0;
int carryout;
while(currl1!=NULL|| currl2!=NULL||carryin!=0)
{
if(currl1==NULL && currl2!=NULL)
{
carryout=addNode(currl2->val,carryin);
currl2=currl2->next;
}
else
{
if(currl2==NULL&& currl1!=NULL)
{
carryout=addNode(currl1->val,carryin);
currl1=currl1->next;
}
else
{
if(currl1!=NULL&& currl2!=NULL)
{
carryout=addNode(currl1->val+currl2->val,carryin);
printf("currl1->val=%d,currl2->val=%d , carryin=%d, carryout=%d\n", currl1->val,currl2->val,carryin,carryout);
currl1=currl1->next;
currl2=currl2->next;
}
else
{
if(currl1==NULL&& currl2==NULL)
{
carryout=addNode(0,carryin);
// printf("currl1->val+currl2->val=%d , carryin=%d\n", currl1->val+currl2->val,carryin);
printf("carryin=%d, carryout=%d\n", carryin,carryout);
}
}

}
}
//printf(" carryout=%d\n",carryout);
carryin=carryout;
}
return head;
}
'''

24 Swap Nodes in Pairs

25 Merge K Sorted Linked Lists

26 Copy List with Random Pointer



