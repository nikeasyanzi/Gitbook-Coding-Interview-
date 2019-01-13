# 2.Math

數學題蠻常考 的數學基本觀念

1. 實作開根號
   1. 牛頓法
   2. binary search \[1, \(x^2\)/2\]
2. 質數表找質數
3. GCD & LCM

```c
int GCD(int a, int b) {
    if(b) while((a %= b) && (b %= a));
    return a + b;
}
int LCM(int a, int b) {
    return a * b / GCD(a, b);
}
```

3 Reserve Integer  
[7. Reserve Integer](/questions/ReverseInteger.md)

4 Plus one  
[66. Plus one](/questions/PlusOne.md)

5 Palindrome Number  
[9. Palindrome Number](/questions/PalindromeNumber.md)

[371. Sum of Two Integers](/questions/questions/SumofTwoIntegers.md)

## [458. Poor Pigs](/questions/PoorPigs.md)

## [69. Sqrt\(x\)](/questions/sqrt.md)

## [914. X of a Kind in a Deck of Cards](/questions/XofaKindinaDeckofCards.md)

## [400. Nth Digit](/questions/NthDigit.md)

### [976.Largest Perimeter Triangle](/questions/LargestPerimeterTriangle.md)



