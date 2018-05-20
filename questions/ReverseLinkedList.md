# [4.Linked List](/LinkedList.md)


#206. Reverse Linked List

    Reverse a singly linked list.
    
    Example:
    
    Input: 1->2->3->4->5->NULL
    Output: 5->4->3->2->1->NULL
    Follow up:
    
    A linked list can be reversed either iteratively or recursively. Could you implement both?

## Recursive

```c

struct ListNode* recursive(struct ListNode* prev,struct ListNode* curr) {
    struct ListNode* head;
    
    if(curr->next!=NULL){
        head=recursive(curr,curr->next);
    }
    
    if(curr->next==NULL){
        head=curr;
    }
        curr->next=prev;

    return head;

}

struct ListNode* reverseList(struct ListNode* head) {
    struct ListNode* curr;
    curr=head;

    if(head==NULL|| head->next==NULL) return head;
    
    head=recursive(curr,curr->next);
    curr->next=NULL; // do forget to point the tail to null


    return head;
}

```
https://leetcode.com/submissions/detail/154996572/


## iterative


```c
struct ListNode* reverseList(struct ListNode* head) {
    struct ListNode* curr;
    curr=head;
    struct ListNode* next;
    struct ListNode* prev;

    if(head==NULL) return NULL;
    next= curr->next;   
    curr->next=NULL; // do forget to point the tail to null
    while(next!=NULL){
        prev=curr;
        curr=next;
        next=curr->next;
        curr->next=prev;
    }  
    
    head=curr; 
    while(curr!=NULL){
        printf("%d", curr->val);
        curr=curr->next;
    }
    
    return head;
}
```

https://leetcode.com/submissions/detail/154924585/


## Reference:
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
