# 4.Linked List

22 Merge Two Sorted Lists [](/questions/MergeTwoSortedLists.md)

23 Add Two Numbers
[2. Add Two Numbers](/questions/AddTwoNumbers.md)


24 Swap Nodes in Pairs

25 Merge K Sorted Linked Lists

26 Copy List with Random Pointer



# Misc:
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
List * loopDetection(List *root){
List *hare=root;
List *tortoise=root;

	while(1){	//loop check
	if(hare==tortise) return true;
    	if(hare==NULL) return false;
    		hare=hare->next;
    	if(hare==NULL) return false;
    		hare=hare->next;
    		tortise=tortise->next;
    	if(hare==tortise) return true;
    }

	hare=root;//find loop entry point
	
	while(hare!=NULL){
		hare=hare->next;
		tortise=tortise->next;
		if(hare==tortise) break;	
	}
	return hare; 
}
```

這個find loop entry
必須在loop detection 完馬上找loop entry point

原理是
hare 回到原點
tortoise 留在原地
兩者一次動一格
再次相遇  即為 loop entry point

loop detection
http://codingfreak.blogspot.com/2012/09/detecting-loop-in-singly-linked-list_22.html

find loop entry
http://codingfreak.blogspot.com/2012/12/detecting-first-node-in-a-loop.html



