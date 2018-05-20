#206. Reverse Linked List



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