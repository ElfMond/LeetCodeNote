# [1] 215. 数组中的第K个最大元素
[leetcode: Nr.167](https://leetcode-cn.com/problems/kth-largest-element-in-an-array/) (easy)

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