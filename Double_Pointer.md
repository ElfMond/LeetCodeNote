# [1] 167. 两数之和 II - 输入有序数组
[leetcode: Nr.167](https://leetcode-cn.com/problems/two-sum-ii-input-array-is-sorted/) (easy)

给定一个已按照升序排列 的有序数组，找到两个数使得它们相加之和等于目标数。

函数应该返回这两个下标值 index1 和 index2，其中 index1 必须小于 index2。

**说明:**

返回的下标值（index1 和 index2）不是从零开始的。
你可以假设每个输入只对应唯一的答案，而且你不可以重复使用相同的元素。

**示例:**
~~~
输入: numbers = [2, 7, 11, 15], target = 9
输出: [1,2]
解释: 2 与 7 之和等于目标数 9 。因此 index1 = 1, index2 = 2 。
~~~

**My Solution**

~~~cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
        int left = 0;
        int right = numbers.size() - 1;
        while(right > left)
        {
            int sum = numbers[left] + numbers[right];
            if(sum == target)
            {
                return {left+1,right+1};
            }
            else if(sum > target) right--;
            else left++;
        }
        return {-1,-1};
    }
};
~~~

# [2] 633. 平方数之和

[leetcode: Nr.633](https://leetcode-cn.com/problems/sum-of-square-numbers/) (easy)

给定一个非负整数 c ，你要判断是否存在两个整数 a 和 b，使得 a2 + b2 = c。

**示例1:**
~~~
输入: 5
输出: True
解释: 1 * 1 + 2 * 2 = 5
~~~

**示例2:**
~~~
输入: 3
输出: False
~~~

**My Solution**
~~~cpp
class Solution {
public:
    bool judgeSquareSum(int c) {
        long right = int(std::sqrt(c));
        long left = 0;
        while(right >= left)
        {
            long sqsum = left*left + right*right;
            if(sqsum == c) return true;
            else if(sqsum < c) left++;
            else right--;
        }
        return false;
    }
};
~~~

# [3] 345. 反转字符串中的元音字母

[leetcode: Nr.345](https://leetcode-cn.com/problems/reverse-vowels-of-a-string/) (easy)

编写一个函数，以字符串作为输入，反转该字符串中的元音字母。

**示例 1:**
~~~
输入: "hello"
输出: "holle"
~~~
**示例 2:**
~~~
输入: "leetcode"
输出: "leotcede"
~~~
**说明:**

元音字母不包含字母"y"。


**My Solution**
~~~cpp
class Solution {
public:
    string reverseVowels(string s) {
        bool dict[256] = {false};
        dict['a'] = true;
        dict['e'] = true;
        dict['i'] = true;
        dict['o'] = true;
        dict['u'] = true;
        dict['A'] = true;
        dict['E'] = true;
        dict['I'] = true;
        dict['O'] = true;
        dict['U'] = true;
        int left = 0;
        int right = s.size()-1;
        while(left < right)
        {
            if(dict[s[left]]&&dict[s[right]])
            {
                char tmp = s[left];
                s[left] = s[right];
                s[right] = tmp;
                left++;right--;
            }
            else if(dict[s[left]]&&(!dict[s[right]]))
                right--;
            else if((!dict[s[left]])&&dict[s[right]])
                left++;
            else 
            {
                left++;right--;
            }
        }
        return s;
    }
};
~~~

# [4] 680. 验证回文字符串 Ⅱ
[leetcode: Nr.680](https://leetcode-cn.com/problems/valid-palindrome-ii/) (easy)

给定一个非空字符串 s，最多删除一个字符。判断是否能成为回文字符串。

**示例 1:**
~~~
输入: "aba"
输出: True
~~~
**示例 2:**
~~~
输入: "abca"
输出: True
解释: 你可以删除c字符。
~~~
**注意:**

字符串只包含从 a-z 的小写字母。字符串的最大长度是50000。


**My Solution**
~~~cpp
class Solution {
public:
    bool validPalindrome(string s) {
        int left = 0;
        int right = s.size()-1;
        while(left<right)
        {
            if(s[left] == s[right])
            {
                left++;right--;
            }
            else
            {
                if(ispal(s,left+1,right)||ispal(s,left,right-1)) return true;
                else return false;
            }
        }
        return true;
    }
    bool ispal(std::string& s,int left,int right)
    {
        while(left<right)
        {
            if(s[left] == s[right])
            {
                left++;right--;
            }
            else return false;
        }
        return true;
    }
};
~~~

# [5] 88. 合并两个有序数组

[leetcode Nr.88](https://leetcode-cn.com/problems/merge-sorted-array/) (easy)

给你两个有序整数数组 nums1 和 nums2，请你将 nums2 合并到 nums1 中，使 nums1 成为一个有序数组。

**说明:**

初始化 nums1 和 nums2 的元素数量分别为 m 和 n 。
你可以假设 nums1 有足够的空间（空间大小大于或等于 m + n）来保存 nums2 中的元素。
 

**示例:**
~~~
输入:
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3

输出: [1,2,2,3,5,6]
~~~

**My Solution**
~~~cpp
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        while(m+n-1 > -1)
        {
            if(n-1 == -1) break;
            else if(m-1 == -1)
            {
                nums1[m+n-1] = nums2[n-1];
                n--;
            }
            else if(nums1[m-1] < nums2[n-1])
            {
                nums1[m+n-1] = nums2[n-1];
                n--;
            }
            else if(nums1[m-1]>=nums2[n-1])
            {
                nums1[m+n-1] = nums1[m-1];
                m--;
            }
        }
    }
};
~~~

# [6] 141. 环形链表


[leetcode Nr.141](https://leetcode-cn.com/problems/linked-list-cycle/) (easy)

给定一个链表，判断链表中是否有环。

为了表示给定链表中的环，我们使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。 如果 pos 是 -1，则在该链表中没有环。

**示例 1：**
~~~
输入：head = [3,2,0,-4], pos = 1
输出：true
解释：链表中有一个环，其尾部连接到第二个节点。
~~~

**示例 2：**
~~~
输入：head = [1,2], pos = 0
输出：true
解释：链表中有一个环，其尾部连接到第一个节点。
~~~

**示例 3：**
~~~
输入：head = [1], pos = -1
输出：false
解释：链表中没有环。
~~~

**进阶：**

你能用 O(1)（即，常量）内存解决此问题吗？


**My Solution**
~~~cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    bool hasCycle(ListNode *head) {
        ListNode* slow = head;
        ListNode* fast = head;
        while((slow != nullptr)&&(fast != nullptr)&&(fast->next != nullptr))
        {
            slow = slow->next;
            fast = fast->next->next;
            if(slow == fast) return true;
        }
        return false;
    }
};
~~~

# [7] 524. 通过删除字母匹配到字典里最长单词

[leetcode Nr.524](https://leetcode-cn.com/problems/longest-word-in-dictionary-through-deleting/) (Medium)

给定一个字符串和一个字符串字典，找到字典里面最长的字符串，该字符串可以通过删除给定字符串的某些字符来得到。如果答案不止一个，返回长度最长且字典顺序最小的字符串。如果答案不存在，则返回空字符串。

**示例 1:**
~~~
输入:
s = "abpcplea", d = ["ale","apple","monkey","plea"]
输出: 
"apple"
~~~
**示例 2:**
~~~
输入:
s = "abpcplea", d = ["a","b","c"]
输出: 
"a"
~~~
**说明:**

* 所有输入的字符串只包含小写字母。
* 字典的大小不会超过 1000。
* 所有输入的字符串长度不会超过 1000。


**My Solution**
~~~cpp
class Solution {
public:
    string findLongestWord(string s, vector<string>& d) {
        std::string res;
        for(std::string di : d)
        {
            int sidx = 0;
            int didx = 0;
            while(sidx < s.size() && didx < di.size())
            {
                if(s[sidx]==di[didx])
                {
                    sidx++;didx++;
                }
                else sidx++;
            }
            if(didx == di.size()) //exist
            {
                res = compareString(res, di);
            }
        }
        return res;
    }
    std::string const compareString(std::string& a,std::string& b) const
    {
        if(a.size()<b.size()) return b;
        else if(a.size()>b.size()) return a;
        else
        {
            int idx = 0;
            while(idx < a.size())
            {
                if(a[idx] < b[idx]) return a;
                else if(a[idx] > b[idx]) return b;
                else idx++;
            }
            return a;
        }
        return a;
    }
};
~~~