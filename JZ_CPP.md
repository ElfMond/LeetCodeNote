# 03. 数组中重复的数字

**题目描述**

找出数组中重复的数字。


在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

**示例 1：**
~~~
输入：
[2, 3, 1, 0, 2, 5, 3]
输出：2 或 3 
~~~

**限制：**
~~~
2 <= n <= 100000
~~~

**解答1: (hash set)**
~~~cpp
class Solution {
public:
    int findRepeatNumber(vector<int>& nums) {
        set<int> hs;
        for (int i = 0 ; i < nums.size() ; i++)
        {
            if(!(hs.insert(nums[i]).second))
                return nums[i];
        }
        return 0;
    }
};
~~~

**解答2: (bool array)**
~~~cpp
class Solution {
public:
    int findRepeatNumber(vector<int>& nums) {
        bool lst[nums.size()] ;
        memset(lst,false,sizeof(lst));
        for (int i = 0; i < nums.size(); i++)
        {
            if (lst[nums[i]])
                return nums[i];
            else
                lst[nums[i]] = true;
        }
        return -1;
    }
};
~~~

# 04. 二维数组中的查找

**题目描述**

在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。


**示例：**

现有矩阵 matrix 如下：
~~~
[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
给定 target = 5，返回 true。
给定 target = 20，返回 false。
~~~

**限制：**
~~~
0 <= n <= 1000
0 <= m <= 1000
~~~

**解答1:**
~~~cpp
class Solution {
public:
    bool findNumberIn2DArray(vector<vector<int>>& matrix, int target) {
        if ( matrix.empty() || matrix[0].empty()) 
            return false;
        else if(matrix[0][0] > target )
        {
            return false;
        }
        else
        {
            for (int i = 0; i < matrix.size(); i++)
            {
                for (int j = 0; j < matrix[i].size(); j++)
                {
                    if (matrix[i][j] == target) 
                        return true;
                    else if (matrix[i][j] > target) 
                        break;
                }
            }
            return false;
        }
        
    }
};
~~~

**解答2:**
~~~cpp
class Solution {
    //从左下角开始找，小则往右，大则往上
public:
    bool findNumberIn2DArray(vector<vector<int>>& matrix, int target) {
        if (matrix.size() == 0){
            return false;
        }
        int m = matrix.size();
        int n = matrix[0].size();
        int row = m - 1;
        int col = 0;
        while (row >=0 && col < n){
            if(matrix[row][col] < target){
                col += 1;
            }
            else if(matrix[row][col] > target){
                row -= 1;
            }
            else{
                return true;
            }
        }
        return false;
    }
};
~~~

