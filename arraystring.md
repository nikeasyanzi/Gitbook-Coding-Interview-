# 3.Array/String

## 6 Two Sum

[tw](//questions/twosum.md)
# 7 Two Sum 2

# 8 Two Sum 3

# 9 Valid Palindrome

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

# 10 STRSTR\(\)

# 11 Reverse words in a string

https://leetcode.com/submissions/detail/147994217/

超機車這題


"abc  def"  -> "def abc"

分成

1. 空白要處理
    1.1移除spaces at tail
    1.2移除spaces at head 
    1.3保留一個space in the text and remove the rest
2. 先反轉每個單字


3. 接者頭尾交換

舉例:
" abc  def "
->
處理空白:"abc def"
->
反轉單字:"cba fed"
->
每個頭尾字元交換:"def abc"

```c
int removeSpace(char *s, int i)
{
    int spaceCount;
    int k;
    int j;
    spaceCount=1;
    while(s[i+spaceCount]==' ')
    {
        spaceCount++;
    }
    k=0;
    while(s[i+k+spaceCount]!='\0')  //lets move forward
    {
        swap(s, i+k,i+k+spaceCount);
        k++;
    }
    s[i+k]='\0';
    j=i+k-1;
    return j;
}
void reverseWords(char *s)
{
    int len=0;
    int j;
    int i=0;
    int k=0;

    j=strlen(s)-1;
    printf("012345678901234567\n");
    printf("%s, len=%d, i=%d,j=%d\n\n",s,strlen(s),i,j);
    while(s[j]==32 & j>=0)    //remove space at tail
    {
        s[j]='\0';
        j--;
    }
    if(s[0]==' ')
    {
        removeSpace(s,0); //remove head space
    }
    while(s[i]!='\0')
    {
        if(s[i]==' ' && s[i+1]== ' ')   //
        {
            removeSpace(s,i+1); //remove middle space
        }
        i++;
    }
    printf("%s, len=%d, i=%d,j=%d\n\n",s,strlen(s),i,j);

    j=0;
    i=0;
    while( s[i]!='\0' )
    {
        i++;
        if (s[i] == '\0')
        {
            reverse(s,j, i-1);
        }
        else if(s[i] == ' ')
        {
            reverse(s,j, i-1);
            j = i+1;
        }
    }
    i=0;
    reverse(s,i,strlen(s)-1);
    printf("%s, len=%d, i=%d,j=%d\n\n",s,strlen(s),i,j);

}
```
Reference:https://www.geeksforgeeks.org/reverse-words-in-a-given-string/



# 12 Reverse words in a string 2

# 13 ATOI

# 14 Valid Number

# 15 Longest Substring Without Repeating Characters

# 16 Longest Substring with At Most Two Distinct Characters

# 17 Missing Ranges

# 18 Longest Palindromic Substring

# 19 One Edit Distance

# 20 Read N Characters Given Read4

# 21 Read N Characters Given Read4 – Call multiple times



不可以用char   要用數字 %10   看可不可以回去



ex. 123321 



digit= val%10 \* 10+ digit

val=val/10



但要考慮結尾為0的case:

12210  -&gt;   012210

### Permutation Sequence

https://leetcode.com/problems/permutation-sequence/description/
http://bangbingsyb.blogspot.tw/2014/11/leetcode-permutation-sequence.html


## permutation


```c
void permute(char *a, int left, int right)
{
   int i;
   if (left == right)
     printf("%s\n", a);
   else
   {
       for (i = left; i <= right; i++)
       {
          swap((a+left), (a+i));
          permute(a, left+1, right);
          swap((a+left), (a+i)); //backtrack
       }
   }
}
```


http://hugedream.blogspot.tw/2009/07/permutation-to-iterate-is-human-to.html
https://www.geeksforgeeks.org/write-a-c-program-to-print-all-permutations-of-a-given-string/


另一種解法是Heap's algorithm 
Why does Heap's algorithm work?
http://ruslanledesma.com/2016/06/17/why-does-heap-work.html
https://www.geeksforgeeks.org/heaps-algorithm-for-generating-permutations/


### interative
http://zhouyichu.com/algorithm/Permutation-Generation-2/


http://www.cnblogs.com/yangykaifa/p/7294929.html
http://l4disgreat.blogspot.tw/2016/02/leet-code-pascals-triangle.html



https://www.geeksforgeeks.org/heaps-algorithm-for-generating-permutations/
http://hugedream.blogspot.tw/2009/07/permutation-to-iterate-is-human-to.html
http://headfirstalgo.blogspot.tw/2016/07/permutation-algorithm.html




