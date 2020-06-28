# [1] 167. Two Sum II - Input array is sorted
[leetcode: Nr.167](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/) (easy)

Given an array of integers that is already ***sorted in ascending order***, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2.

**Note:**
* Your returned answers (both index1 and index2) are not zero-based.
* You may assume that each input would have *exactly* one solution and you may not use the *same* element twice.

**Example**
<pre>
<b>Input:</b> number = [2,7,11,15], target = 9
<b>Output:</b> [1,2]
<b>Explanation:</b> The sum of 2 and 7 is 9. Therefore index1 = 1, index2 = 2.
</pre>

**My Solution**

~~~python
# Version 1
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        dct = {}
        for idx,num in enumerate(numbers):
            if num in dct:
                return [dct[num] + 1, idx + 1]
            else:
                dct[target - num] = idx
# Version 2
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        i = 0;j = len(numbers)-1
        while i<j:
            if numbers[i]+numbers[j]==target:
                return [i+1,j+1]
            elif numbers[i]+numbers[j]>target:
                j = j-1
            elif numbers[i]+numbers[j]<target:
                i = i+1
~~~

**Explanation**

only one loop, store the desired pair number as key in a dictionary.

# [2] 633. Sum of Square Numbers

[leetcode: Nr.633](https://leetcode.com/problems/sum-of-square-numbers/description/) (easy)

Given a non-negative integer c, your task is to decide whether there're two integers a and b such that $a^2 + b^2 = c$.

**Example 1:**
<pre>
<b>Input:</b> 5
<b>Output:</b> True
<b>Explanation:</b> 1 * 1 + 2 * 2 = 5
</pre>

**Example 2:**
<pre>
<b>Input:</b> 3
<b>Output:</b> False
</pre>

**My Solution**

~~~python
class Solution:
    def judgeSquareSum(self, c: int) -> bool:
        i = 0; j = int(math.sqrt(c))
        while i<=j:
            if i*i+j*j == c:
                return True
            elif i*i+j*j < c:
                i=i+1
            elif i*i+j*j > c:
                j=j-1
        return False  
~~~

# [3] 345. Reverse Vowels of a String

[leetcode: Nr.345](https://leetcode.com/problems/reverse-vowels-of-a-string/description/) (easy)

Write a function that takes a string as input and reverse only the vowels of a string.

**Example 1:**
<pre>
<b>Input:</b> 5
<b>Output:</b> True
<b>Explanation:</b> 1 * 1 + 2 * 2 = 5
</pre>

**Example 2:**
<pre>
<b>Input:</b> 3
<b>Output:</b> False
</pre>

**My Solution**
~~~python
class Solution:
    def reverseVowels(self, s: str) -> str:
        lst = list(s)
        i = 0
        j = len(lst) - 1
        vowels = ['a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U']
        while i < j:
            if (lst[i] in vowels) and (lst[j] in vowels):
                tmp = lst[i]
                lst[i] = lst[j]
                lst[j] = tmp
                i = i + 1
                j = j - 1
            elif (lst[j] not in vowels):
                j = j - 1
            elif (lst[i] not in vowels):
                i = i + 1
        return "".join(lst)
~~~

**Better Solution**
~~~python
class Solution:
    def reverseVowels(self, s: str) -> str:
        vowels = [x for x in s if x in 'aeiouAEIOU']
        idx = [i for i in range(len(s)) if s[i] in 'aeiouAEIOU']
        vowels = vowels[::-1]
        x = 0
        s = list(s)
        for i in idx:
            s[i] = vowels[x]
            x+=1
        return ''.join(s)
~~~

# [4] 680.Valid Palindrome II
[leetcode: Nr.680](https://leetcode.com/problems/valid-palindrome-ii/) (easy)

Given a non-empty string s, you may delete **at most** one character. Judge whether you can make it a palindrome.

**Example 1:**
<pre>
<b>Input:</b> "aba"
<b>Output:</b> True
</pre>
**Example 2:**
<pre>
<b>Input:</b> "abca"
<b>Output:</b> True
<b>Explanation:</b> You could delete the character 'c'.
</pre>

**My Solution**
~~~python
class Solution:
    def validPalindrome(self, s: str) -> bool:
        i = 0
        j = len(s) -1
        while i < j:
            if s[i] != s[j]:
                str1 = s[i+1:j+1]
                str2 = s[i:j]
                if str1 != str1[::-1] and str2 != str2[::-1]:
                    return False
            i = i + 1
            j = j - 1
        return True
~~~

**Better Solution**
~~~python
def validPalindrome(self, s: str) -> bool:
    def verify(s, left, right, deleted):
        while left < right:
            if s[left] != s[right]:
                if deleted:
                    return False
                else:
                    return verify(s, left+1, right, True) or verify(s, left, right-1, True)
            else:
                left += 1
                right -= 1
        return True
    return verify(s, 0, len(s)-1, False)
~~~

# [5] 88. Merge Sorted Array

[leetcode Nr.88](https://leetcode.com/problems/merge-sorted-array/) (easy)

Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

**Note:**
* The number of elements initialized in *nums1* and *nums2* are m and n respectively.
* You may assume that *nums1* has enough space (size that is greater or equal to m + n) to hold additional elements from *nums2*.
  
**Example**
<pre>
<b>Input:</b>
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3
<b>Output:</b> [1,2,2,3,5,6]
</pre>

**My Solution**
~~~python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        i = m - 1
        j = n - 1
        last = m + n -1
        while i >= 0 or j >= 0 :
            if i < 0:
                nums1[last] = nums2[j]
                last = last - 1
                j = j - 1
            elif j < 0:
                nums1[last] = nums1[i]
                last = last - 1
                i = i - 1
            elif nums1[i] <= nums2[j]:
                nums1[last] = nums2[j]
                last = last - 1
                j = j - 1
            elif nums1[i] > nums2[j]:
                nums1[last] = nums1[i]
                i = i - 1
                last = last - 1
~~~