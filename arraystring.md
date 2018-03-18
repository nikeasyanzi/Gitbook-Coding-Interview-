# 3.Array/String

\#\# 6 Two Sum

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

    Example:
    Given nums = [2, 7, 11, 15], target = 9,
    
    Because nums[0] + nums[1] = 2 + 7 = 9,
    return [0, 1].

```c
int  *result=NULL;


int* twoSum(int* nums, int numsSize, int target)
{
    int *hash;

    int i;
    int min=INT_MAX;
    int max=INT_MIN;
    result=malloc(sizeof(int)*2); 

    result[0]=-1;
    result[1]=-1;


    for (i=0; i<numsSize; i++)
    {
        if(nums[i]<min) min=nums[i];
        if(nums[i]>max) max=nums[i];
    }

    hash=malloc(sizeof(int)*(max-min+1));
    for (i=0; i<max-min+1; i++)
    {
        hash[i]=-1;
    }

    for(i=0; i<numsSize; i++)
    {
        //printf("i=%d target-nums=%d\n",i,target-nums[i]);

        if( hash[nums[i]-min]!=-1 && i != hash[nums[i]-min])
        {
            result[0]=i;
            result[1]=hash[nums[i]-min];
        }else{
            hash[target-nums[i]-min]=i;         //the ith element needs target-nums[i]
        }

    }

    return result;
}

```

這題  測資都過了  但 submit 過不了  好奇怪

    int A[3]= {3,2,4};  //6

    int B[2]= {3,3}; //6
    int C[5]={-1,-2,-3,-4,-5}; //-8
    int D[4]={-3,4,3,90}; //0
    int E[4]={0,4,3,0};//0

這題解法

1.暴力法  兩個迴圈  O(N^2)

2.用hash table
也就是說

    2.1假設n個數 其中的max & min 為hash table的大小

    這個hash table 就很有學問
    
    必須以一般的max & min作為hash table範圍

        ex. target=30
       最大數 max(n)=30
       最小數 min(n)=-20    
    
    理論上hash 應該在-20 ~30 
    
    所以 hashtable為  max ~ min    
    

 
    
  2.2若對某數n  , 紀錄hash [target-n ]是被需要的
 
       
       1.紀錄該數n的index
       
        hash[index] 這行不通
        因為之後我們是用target-n 來檢查的
        
     2.只能紀錄
     
         hash[target-n] 
  
    
    3.考慮紀錄
    hash[target-n]=0/1;
    target-n 是否有被需要
    
    表示target-n 有缺   但題目要回傳index 所以不行
    
    
    4.考慮紀錄index
     hash[target-n]=某數n 的index (ok)
    target-n被n需要
    
    5.之後檢查  兩數的index 必不相同
    target=6 [3,4,0,3]
    
    
    


\#\# 7 Two Sum 2

\#\# 8 Two Sum 3

\#\# 9 Valid Palindrome

```c
int isAlphbat(char a)
{
    if((a>='a' && a<='z')||(a>='A' && a<='Z') )
    {
        return true;
    }
    return false;
}

int isDigit(char a)
{
    if((a>='0' && a<='9') )
    {
        return true;
    }
    return false;
}
int cmp(char a,char b)
{
    if(isAlphbat(a)&& isAlphbat(b))
    {
        if(a==b )
            return true;

        if((a>b && a-b=='a'-'A' ) || (a<b && b-a=='a'-'A'))
            return true;
    }
    else
    {
        if(isDigit(a)&& isDigit(b))
        {
            if(a==b )
                return true;
        }
    }
    return false;

}

bool isPalindrome(char *s)
{
    char *head=s;
    char *tail=head+strlen(s)-1;
    if (s==NULL)    //null case
    {
        return true;
    }
    while(head<tail)
    {
        while(!isAlphbat(*head) && !isDigit(*head))//get the first alphbat or digit
            head++;

        while(!isAlphbat(*tail) && !isDigit(*tail))//get the latest alphbat or digit
            tail--;
        if( !cmp(*head,*tail) && head<= tail)
        {
            return false;
        }
        else
        {
            head++;
            tail--;
        }
    }
    return true;
}

```

1.這題只要考慮  字母  與數字  其他符號可忽略不考慮

    所以必須分別寫出 isAlphbat & isDigit
    
    把字母跟數字混著一起考慮  會讓狀況更亂
    
2.分別用兩個指標  指向head & tail 

    1. 如果兩個Character 是字母
            則忽略大小寫  並判別是否想相同
    
    2. 如果兩個Character 是數字
          判別是否相同

3.終止條件就是tail>head囉

測資:
     char *ss="a.";  //true
     char *sss="aA"; //true
     char *ssss="0P"; //false


4.

看到有人這樣寫  用if + continue  其實這樣比較好   我原本寫的多個while 很容易讓人誤會

```c
while(head<tail)
{
    //while(!isAlphbat(*head) && !isDigit(*head))//get the first alphbat or digit
    //    head++;
    if(!isAlphbat(*head) && !isDigit(*head))//get the first alphbat or digit
        head++;
        continue;
        
    //while(!isAlphbat(*tail) && !isDigit(*tail))//get the latest alphbat or digit
    //    tail--;
    if(!isAlphbat(*tail) && !isDigit(*tail))//get the latest alphbat or digit
        head--;
        continue;
}
```

\#\# 10 STRSTR\(\)

\#\# 11 Reverse words in a string

\#\# 12 Reverse words in a string 2

\#\# 13 ATOI

\#\# 14 Valid Number

\#\# 15 Longest Substring Without Repeating Characters

\#\# 16 Longest Substring with At Most Two Distinct Characters

\#\# 17 Missing Ranges

\#\# 18 Longest Palindromic Substring

\#\# 19 One Edit Distance

\#\# 20 Read N Characters Given Read4

\#\# 21 Read N Characters Given Read4 – Call multiple times



不可以用char   要用數字 %10   看可不可以回去



ex. 123321 



digit= val%10 \* 10+ digit

val=val/10



但要考慮結尾為0的case:

12210  -&gt;   012210

Permutation Sequence

https://leetcode.com/problems/permutation-sequence/description/
http://bangbingsyb.blogspot.tw/2014/11/leetcode-permutation-sequence.html


## permutation

程式語言建立自信系列-排列 part 1(
https://home.gamer.com.tw/creationDetail.php?sn=3211869

Why does Heap's algorithm work?
http://ruslanledesma.com/2016/06/17/why-does-heap-work.html

### interative
http://zhouyichu.com/algorithm/Permutation-Generation-2/


http://www.cnblogs.com/yangykaifa/p/7294929.html
http://l4disgreat.blogspot.tw/2016/02/leet-code-pascals-triangle.html



https://www.geeksforgeeks.org/heaps-algorithm-for-generating-permutations/
http://hugedream.blogspot.tw/2009/07/permutation-to-iterate-is-human-to.html
http://headfirstalgo.blogspot.tw/2016/07/permutation-algorithm.html




