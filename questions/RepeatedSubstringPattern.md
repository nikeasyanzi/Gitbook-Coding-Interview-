# [3. Array/String](/arraystring.md)

[459. Repeated Substring Pattern](https://leetcode.com/problems/repeated-substring-pattern/)


'''python
class Solution:
    def repeatedSubstringPattern(self, s):
        """
        :type s: str
        :rtype: bool
        
        """

        if not str:
            return False
            
        ss = (s + s)[1:-1]
        return ss.find(s) != -1
'''


解法1. 暴力法

從2 ~ len(string)/2 的區間 找len(string)/2的因數
因為要為因數才有辦法組合成repeated substring
針對每個因數下去檢查


ex. abcdefg

解法2.
把原本string 疊合 一次 取中間字串與原本字串做檢查

between 1 and -1 倒數一 is becasue when input s is a char ex. "a"
ex.
s=a ss=""
s=abab ss=aa

## Reference:
https://windsuzu.github.io/leetcode-459/




