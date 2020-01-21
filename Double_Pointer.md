# 167. Two Sum II - Input array is sorted
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
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        dct = {}
        for idx,num in enumerate(numbers):
            if num in dct:
                return [dct[num] + 1, idx + 1]
            else:
                dct[target - num] = idx
~~~
