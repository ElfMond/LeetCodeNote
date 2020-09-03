# [1] 215. 数组中的第K个最大元素
[leetcode: Nr.167](https://leetcode-cn.com/problems/kth-largest-element-in-an-array/) (medium)

在未排序的数组中找到第 k 个最大的元素。请注意，你需要找的是数组排序后的第 k 个最大的元素，而不是第 k 个不同的元素。

**示例 1:**
~~~
输入: [3,2,1,5,6,4] 和 k = 2
输出: 5
~~~
**示例 2:**
~~~
输入: [3,2,3,1,2,4,5,5,6] 和 k = 4
输出: 4
~~~
**说明:**

你可以假设 k 总是有效的，且 1 ≤ k ≤ 数组的长度。


**My Solution**

~~~cpp
//16ms,10.2MB
class Solution {
public:
    int findKthLargest(vector<int>& nums, int k) {
        std::vector<int> heap(k,0);
        for(int i = 0;i<k;i++)  heap[i] = nums[i];
        std::make_heap(heap.begin(),heap.end(),std::greater<>{});
        for(int idx = k;idx<nums.size();idx++)
        {
            if(nums[idx]>heap[0])
            {
                std::pop_heap(heap.begin(),heap.end(),std::greater<>{});
                heap.pop_back();
                heap.push_back(nums[idx]);
                std::push_heap(heap.begin(),heap.end(),std::greater<>{});
            }
        }
        return heap[0];
    }
};
~~~
~~~cpp
//12ms,9.8MB 就地建堆
class Solution {
public:
    int findKthLargest(vector<int>& nums, int k) {
        std::make_heap(nums.begin(),nums.begin()+k,std::greater<>{});
        for(int idx = k;idx < nums.size();idx++)
        {
            std::swap(nums[k],nums[idx]);
            if(nums[k] > nums[0])
            {
                std::pop_heap(nums.begin(),nums.begin()+k,std::greater<>{});
                std::swap(nums[k-1],nums[k]);
                std::push_heap(nums.begin(),nums.begin()+k,std::greater<>{});
            }
        }
        return nums[0];
    }
};
~~~
~~~cpp
//20ms,10MB std::priority_queue
class Solution {
public:
    int findKthLargest(vector<int>& nums, int k) {
        std::priority_queue<int,std::vector<int>,std::greater<int>> pq;
        for(int idx = 0;idx < nums.size();idx++)
        {
            if(pq.size() != k) pq.push(nums[idx]);
            else if(pq.top() < nums[idx])
            {
                pq.pop();
                pq.push(nums[idx]);
            }
        }
        return pq.top();
    }
};
~~~


# [2] 347. 前 K 个高频元素
[leetcode: Nr.347](https://leetcode-cn.com/problems/top-k-frequent-elements/) (medium)

给定一个非空的整数数组，返回其中出现频率前 k 高的元素。

**示例 1:**
~~~
输入: nums = [1,1,1,2,2,3], k = 2
输出: [1,2]
~~~
**示例 2:**
~~~
输入: nums = [1], k = 1
输出: [1]
~~~

**提示：**

* 你可以假设给定的 k 总是合理的，且 1 ≤ k ≤ 数组中不相同的元素的个数。
* 你的算法的时间复杂度必须优于 O(n log n) , n 是数组的大小。
* 题目数据保证答案唯一，换句话说，数组中前 k 个高频元素的集合是唯一的。
* 你可以按任意顺序返回答案。

**My Solution**

~~~cpp
class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) {
        std::unordered_map<int,int> mymap;
        for(int num : nums) mymap[num]++;
        auto cmp = [&](int a,int b) {return (mymap[a]>mymap[b]);};
        std::priority_queue<int,std::vector<int>,decltype(cmp)> pq(cmp);
        for(auto num : mymap)
        {
            if(pq.size()<k) pq.push(num.first);
            else if(cmp(num.first,pq.top()))
            {
                pq.pop();
                pq.push(num.first);
            }
        }
        std::vector<int> res(k,0);
        for(int i = 0;i < k;i++) 
        {
            res[i] = pq.top();
            pq.pop();
        }
        return res;
    }
};
~~~


# [3] 451. 根据字符出现频率排序
[leetcode: Nr.451](https://leetcode-cn.com/problems/sort-characters-by-frequency/) (medium)

给定一个字符串，请将字符串里的字符按照出现的频率降序排列。

**示例 1:**
~~~
输入:
"tree"

输出:
"eert"

解释:
'e'出现两次，'r'和't'都只出现一次。
因此'e'必须出现在'r'和't'之前。此外，"eetr"也是一个有效的答案。
~~~
**示例 2:**
~~~
输入:
"cccaaa"

输出:
"cccaaa"

解释:
'c'和'a'都出现三次。此外，"aaaccc"也是有效的答案。
注意"cacaca"是不正确的，因为相同的字母必须放在一起。
~~~
**示例 3:**
~~~
输入:
"Aabb"

输出:
"bbAa"

解释:
此外，"bbaA"也是一个有效的答案，但"Aabb"是不正确的。
注意'A'和'a'被认为是两种不同的字符。
~~~

**My Solution**
~~~cpp
class Solution {
public:
    string frequencySort(string s) {
        std::unordered_map<char,int> count;
        for(auto e : s) count[e]++;
        auto cmp =[&](char a,char b){return count[a]<count[b];};
        std::priority_queue<char,std::vector<char>,decltype(cmp)> pq(cmp);
        for(auto e : count) pq.push(e.first);
        std::string res;
        while(pq.size())
        {
            for(int i = 0;i < count[pq.top()];i++)
                res += pq.top();
            pq.pop();
        }
        return res;
    }
};
~~~


# [4] 75. 颜色分类
[leetcode: Nr.451](https://leetcode-cn.com/problems/sort-colors/) (medium)

给定一个包含红色、白色和蓝色，一共 n 个元素的数组，原地对它们进行排序，使得相同颜色的元素相邻，并按照红色、白色、蓝色顺序排列。

此题中，我们使用整数 0、 1 和 2 分别表示红色、白色和蓝色。

**注意:**
不能使用代码库中的排序函数来解决这道题。

**示例:**
~~~
输入: [2,0,2,1,1,0]
输出: [0,0,1,1,2,2]
~~~
**进阶：**

一个直观的解决方案是使用计数排序的两趟扫描算法。
首先，迭代计算出0、1 和 2 元素的个数，然后按照0、1、2的排序，重写当前数组。
你能想出一个仅使用常数空间的一趟扫描算法吗？

**My Solution**
~~~cpp
class Solution {
public:
    void sortColors(vector<int>& nums) {
        int zero = 0;
        int two = 0;
        for(int i = 0;i < nums.size()-two;i++)
        {
            if(nums[i] == 0)
            {
                if(i == zero) 
                {
                    zero++;
                    continue;
                }
                std::swap(nums[zero],nums[i]);
                zero++;
                i--;
            }
            else if(nums[i] == 2)
            {
                if(i == nums.size()-two-1) 
                {
                    two++;
                    continue;
                }
                std::swap(nums[i],nums[nums.size()-two-1]);
                two++;
                i--;
            }
        }
    }
};
~~~