# [4.Linked List](/LinkedList.md)

# 141. Linked List Cycle



https://leetcode.com/submissions/detail/155181105/




# 142. Linked List Cycle II

https://leetcode.com/submissions/detail/155357605/

```c
struct ListNode *detectCycle(struct ListNode *head) {
    struct ListNode *tortise;
    struct ListNode *hare;
    
    tortise=head;
    hare=head;
    if(tortise==NULL || tortise->next==NULL ) return false;
    while( tortise!=NULL){
        if(tortise->next!=NULL)
        {
            tortise=tortise->next;
        }
        hare=hare->next;
            tortise=tortise->next;
            if(tortise==hare) break; 
    }
    if(tortise==NULL) return NULL;
    tortise=head;
    while(tortise!=hare){
        tortise=tortise->next;
        hare=hare->next;
    }
    
    return hare;
}
```