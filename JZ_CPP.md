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

# 05. 替换空格

**题目描述**

请实现一个函数，把字符串 s 中的每个空格替换成"%20"。

**示例：**
~~~
输入：s = "We are happy."
输出："We%20are%20happy."
~~~

**限制：**
~~~
0 <= s 的长度 <= 10000
~~~

**解答1:**
~~~cpp
class Solution {
public:
    string replaceSpace(string s) {
        string res;
        for (int i = 0;i < s.size(); i++)
        {
            if(s[i] == ' ')
                res += "%20";
            else
                res += s[i];
        }
        return res;
    }
};
~~~

# 06. 从尾到头打印链表

**题目描述**

输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。

**示例：**
~~~
输入：head = [1,3,2]
输出：[2,3,1]
~~~

**限制：**
~~~
0 <= 链表长度 <= 10000
~~~

**解答1:**
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
    vector<int> reversePrint(ListNode* head) {
        vector<int> res;
        if(head != NULL)
        {
            res.push_back((*head).val);
            head = (*head).next;
        }
        while (head != NULL)
        {
            res.insert(res.begin(),(*head).val);
            head = (*head).next;
        }
        return res;
    }
};
~~~

**解答2:**
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
    vector<int> reversePrint(ListNode* head) {
        vector<int> res;
        while (head != NULL)
        {
            res.push_back(head->val);
            head = head->next;
        }

        reverse(res.begin(),res.end());
        return res;
    }
};
~~~

# 07. 重建二叉树

**题目描述**

输入某二叉树的前序遍历和中序遍历的结果，请重建该二叉树。假设输入的前序遍历和中序遍历的结果中都不含重复的数字。

**示例：**

例如，给出
~~~
前序遍历 preorder = [3,9,20,15,7]
中序遍历 inorder = [9,3,15,20,7]
~~~
返回如下的二叉树：
~~~
    3
   / \
  9  20
    /  \
   15   7
~~~

**限制：**
~~~
0 <= 节点个数 <= 5000
~~~

**解答1:**
~~~cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        return recu(preorder.begin(),preorder.end(),inorder.begin(),inorder.end());
    }
    TreeNode* recu(vector<int>::iterator headPre, vector<int>::iterator rearPre, vector<int>::iterator headIn ,vector<int>::iterator rearIn)
    {
        if (headPre== rearPre)  return NULL;
        TreeNode* cur = new TreeNode(*headPre);
        auto root = find(headIn,rearIn,*headPre);
        cur->left = recu(headPre+1,headPre + 1 + (root -headIn),headIn,root);
        cur->right = recu(headPre + 1 + (root -headIn),rearPre,root+1,rearIn);
        return cur;
    }
};
~~~
~~~
前序遍历的首个元素即为根节点 root 的值；
在中序遍历中搜索根节点 root 的索引 ，可将中序遍历划分为 [ 左子树 | 根节点 | 右子树 ] 。
根据中序遍历中的左（右）子树的节点数量，可将前序遍历划分为 [ 根节点 | 左子树 | 右子树 ] 。
~~~