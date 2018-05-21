# 4.Linked List

22 Merge Two Sorted Lists [](/questions/MergeTwoSortedLists.md)

23 Add Two Numbers
[2. Add Two Numbers](/questions/AddTwoNumbers.md)


24 Swap Nodes in Pairs

25 Merge K Sorted Linked Lists

26 Copy List with Random Pointer


# Misc:

[206. Reverse Linked List](/questions/ReverseLinkedList.md)


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

https://leetcode.com/problems/linked-list-cycle/description/

1,cycle detection 重點在交錯式
要tortise 走一步hare 檢查是不是到終點
再走第二部
這是因為考慮   沒有cycle的狀況下

2. 邊界條件就是 list is empty 直接return false  (no cycle)

