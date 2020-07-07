<a href="#index"></a>
<a href="#03">03. 数组中重复的数字</a>  
<a href="#04">04. 二维数组中的查找</a>  
<a href="#05">05. 替换空格</a>  
<a href="#06">06. 从尾到头打印链表</a>  
<a href="#07">07. 重建二叉树</a>  
<a href="#09">09. 用两个栈实现队列</a>  
<a href="#10-I">10-I. 用两个栈实现队列</a>  
<a href="#10-II">10-II. 青蛙跳台阶问题</a>  
<a href="#11">11. 旋转数组的最小数字</a>  
<a href="#12">12. 矩阵中的路径</a>  
<a href="#16">16. 数值的整数次方</a>  
<a href="#25">25. 合并两个排序的链表</a>  
<a href="#29">29. 顺时针打印矩阵</a>  
<a href="#30">30. 包含min函数的栈</a>  
<a href="#53-I">53-I. 在排序数组中查找数字</a>  
<a href="#53-II">53-II. 0～n-1中缺失的数字</a>  
<a href="#59">59-II. 队列的最大值</a>  


# <a name="03">03. 数组中重复的数字</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

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

# <a name="04">04. 二维数组中的查找</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

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

# <a name="05">05. 替换空格</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

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

# <a name="06">06. 从尾到头打印链表</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

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

# <a name="07">07. 重建二叉树</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

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

# <a name="09">09. 用两个栈实现队列</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，deleteHead 操作返回 -1 )


**示例1：**

例如，给出
~~~
输入：
["CQueue","appendTail","deleteHead","deleteHead"]
[[],[3],[],[]]
输出：[null,null,3,-1]

~~~

**示例2：**
~~~
输入：
["CQueue","deleteHead","appendTail","appendTail","deleteHead","deleteHead"]
[[],[],[5],[2],[],[]]
输出：[null,-1,null,null,5,2]
~~~

**提示：**

* 1 <= values <= 10000
* 最多会对 appendTail、deleteHead 进行 10000 次调用


**解答:**
~~~cpp
class CQueue {
public:
    stack<int> st1;
    stack<int> st2;
    CQueue() {

    }
    
    void appendTail(int value) {
        st1.push(value);
    }
    
    int deleteHead() {
        if(st1.empty()) return -1;
        while(!st1.empty())
        {
            st2.push(st1.top());
            st1.pop();
        }
        int ret = st2.top();
        st2.pop();
        while(!st2.empty())
        {
            st1.push(st2.top());
            st2.pop();
        }
        return ret;
    }
};

/**
 * Your CQueue object will be instantiated and called as such:
 * CQueue* obj = new CQueue();
 * obj->appendTail(value);
 * int param_2 = obj->deleteHead();
 */
~~~


# <a name="10-I">10-I. 用两个栈实现队列</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

写一个函数，输入 n ，求斐波那契（Fibonacci）数列的第 n 项。斐波那契数列的定义如下：
~~~
F(0) = 0,   F(1) = 1
F(N) = F(N - 1) + F(N - 2), 其中 N > 1.
~~~
斐波那契数列由 0 和 1 开始，之后的斐波那契数就是由之前的两数相加而得出。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。


**示例1：**

例如，给出
~~~
输入：n = 2
输出：1
~~~

**示例2：**
~~~
输入：n = 5
输出：5
~~~

**提示：**

* 0 <= n <= 100


**解答:**
~~~cpp
class Solution {
public:
    int fib(int n) {
        int pre = 1;
        int prepre = 0;
        if(n < 2) return n;
        for(int idx = 1;idx < n;idx++)
        {
            pre = prepre + pre;
            prepre = pre -prepre;
            pre %= 1000000007;
        }
        return pre;
    }
};
~~~


# <a name="10-II">10-II. 青蛙跳台阶问题</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

一只青蛙一次可以跳上1级台阶，也可以跳上2级台阶。求该青蛙跳上一个 n 级的台阶总共有多少种跳法。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。

**示例1：**

例如，给出
~~~
输入：n = 2
输出：2
~~~

**示例2：**
~~~
输入：n = 7
输出：21
~~~

**提示：**

* 0 <= n <= 100


**解答:**
~~~cpp
class Solution {
public:
    int numWays(int n) {
        if(n < 3) return n == 0? 1:n;
        int pre = 2, prepre = 1;
        for(int idx = 2;idx < n;idx++)
        {
            pre = pre + prepre;
            prepre = pre - prepre;
            pre %= 1000000007;
        }
        return pre;
    }
};
~~~

# <a name="11">11. 旋转数组的最小数字</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。输入一个递增排序的数组的一个旋转，输出旋转数组的最小元素。例如，数组 [3,4,5,1,2] 为 [1,2,3,4,5] 的一个旋转，该数组的最小值为1。  

**示例1：**

例如，给出
~~~
输入：[3,4,5,1,2]
输出：1
~~~

**示例2：**
~~~
输入：[2,2,2,0,1]
输出：0
~~~


**解答1:**
~~~cpp
class Solution {
public:
    int minArray(vector<int>& numbers) {
        for(int idx = 0;idx <numbers.size() - 1;idx++ )
        {
            if(numbers[idx + 1] < numbers[idx])
                return numbers[idx + 1];
        }
        return numbers[0];
    }
};
~~~


**解答2:**
~~~cpp
class Solution {
public:
    int minArray(vector<int>& numbers) {
        int left = 0, right = numbers.size() - 1;
        while(left < right)
        {
            int mid = (left + right) >> 1;
            if(numbers[right] < numbers[mid])  left = mid + 1;
            else if(numbers[mid] == numbers[right]) right --;
            else right = mid;
        } 
        return numbers[left];
    }
};
~~~


# <a name="12">12. 矩阵中的路径</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

请设计一个函数，用来判断在一个矩阵中是否存在一条包含某字符串所有字符的路径。路径可以从矩阵中的任意一格开始，每一步可以在矩阵中向左、右、上、下移动一格。如果一条路径经过了矩阵的某一格，那么该路径不能再次进入该格子。例如，在下面的3×4的矩阵中包含一条字符串“bfce”的路径（路径中的字母用加粗标出）。

[["a","**b**","c","e"],

["s","**f**","**c**","s"],

["a","d","**e**","e"]]

但矩阵中不包含字符串“abfb”的路径，因为字符串的第一个字符b占据了矩阵中的第一行第二个格子之后，路径不能再次进入这个格子。


**示例1：**

例如，给出
~~~
输入：board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
输出：true

~~~

**示例2：**
~~~
输入：board = [["a","b"],["c","d"]], word = "abcd"
输出：false
~~~


**解答1:**
~~~cpp
class Solution {
public:
    bool exist(vector<vector<char>>& board, string word) {
        for(int i = 0;i < board.size();i ++)
        {
            for(int j = 0; j < board[0].size(); j++)
            {
                if(board[i][j] == word[0])
                {
                    vector<vector<char>> board_copy = board;
                    string word_copy = word;
                    if(recf(board_copy,word_copy.erase(0,1),i,j)) return true;
                }
            }
        }
        return false;
    }
    bool recf(vector<vector<char>> board, string word,int i,int j)
    {
        if(word.size() == 0) return true;
        board[i][j] = '/';
        if(i-1>=0 && board[i-1][j] == word[0])
        {
            string word_copy = word;
            if(recf(board,word_copy.erase(0,1),i-1,j)) return true;
        }
        if(i+1<board.size() && board[i+1][j] == word[0])
        {
            string word_copy = word;
            if(recf(board,word_copy.erase(0,1),i+1,j)) return true;
        }
        if(j-1>=0 && board[i][j-1] == word[0])
        {
            string word_copy = word;
            if(recf(board,word_copy.erase(0,1),i,j-1)) return true;
        }
        if(j+1 < board[0].size() && board[i][j+1] == word[0])
        {
            string word_copy = word;
            if(recf(board,word_copy.erase(0,1),i,j+1)) return true;
        }
        return false;
    }
};
~~~


**解答2:**
~~~cpp

~~~



# <a name="16">16. 数值的整数次方</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

实现函数double Power(double base, int exponent)，求base的exponent次方。不得使用库函数，同时不需要考虑大数问题。


**示例1：**

~~~
输入: 2.00000, 10
输出: 1024.00000

~~~

**示例2：**
~~~
输入: 2.10000, 3
输出: 9.26100
~~~

**示例3：**
~~~
输入: 2.00000, -2
输出: 0.25000
解释: 2-2 = 1/22 = 1/4 = 0.25
~~~

**解答1:**
~~~cpp
class Solution {
public:
    double myPow(double x, int n) {
        if(n==0||x==1) return 1;
        if(x==0) return 0;
        long num = n;
        double res = 1;
        if(n < 0) 
        {
            x = 1/x;
            num = -num;
        }
        while(num)
        {
            if(num&1) res *= x;
            x *= x;
            num >>= 1;
        }
        return res;
    }
};
~~~



# <a name="25">25. 合并两个排序的链表</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

输入两个递增排序的链表，合并这两个链表并使新链表中的节点仍然是递增排序的。


**示例1：**

~~~
输入：1->2->4, 1->3->4
输出：1->1->2->3->4->4

~~~

限制：
~~~
0 <= 链表长度 <= 1000
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
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        ListNode* res = new ListNode(0);
        ListNode* current = res;
        while(l1 != nullptr && l2 != nullptr)
        {
            if(l1->val <= l2->val)
            {
                current->next = l1;
                l1 = l1->next;
            }
            else
            {
                current->next = l2;
                l2 = l2->next;
            }
            current = current->next;
        }
        current->next = (l1 == nullptr)? l2:l1;
        return res->next;
    }
};
~~~



# <a name="29">29. 顺时针打印矩阵</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字。

**示例：**

~~~
输入：matrix = [[1,2,3],[4,5,6],[7,8,9]]
输出：[1,2,3,6,9,8,7,4,5]
~~~

**限制**

* 0 <= matrix.length <= 100
* 0 <= matrix[i].length <= 100

**解答1:**
~~~cpp
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        std::vector<int> res;
        if(matrix.empty()) return res;
        int left = 0,right = matrix[0].size() - 1,up = 0,down = matrix.size() - 1;
        int row = 0 , col = 0;
        while(true)
        {
            for( ;col <= right;col++)
            {
                res.push_back(matrix[row][col]);
            }
            col--; up++;
            if(row + 1> down) break;
            row++;
            for(;row <= down;row++)
            {
                res.push_back(matrix[row][col]);
            }
            row--; right--;
            if(col - 1 < left) break;
            col--;
            for(;col >= left;col--)
            {
                res.push_back(matrix[row][col]);
            }
            col++; down--;
            if(row - 1 < up) break;
            row--;
            for(;row >= up;row--)
            {
                res.push_back(matrix[row][col]);
            }
            row++; left++;
            if(col + 1 > right) break;
            col++;
        }
        return res;
    }
};
~~~



# <a name="30">30. 包含min函数的栈</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的 min 函数在该栈中，调用 min、push 及 pop 的时间复杂度都是 O(1)。


**示例：**

~~~
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.min();   --> 返回 -3.
minStack.pop();
minStack.top();      --> 返回 0.
minStack.min();   --> 返回 -2.

~~~



**解答1:**
~~~cpp
class MinStack {
public:
    /** initialize your data structure here. */
    int min_val;
    std::stack<std::pair<int,int>> stk;
    MinStack() {
        min_val = INT_MAX;
    }
    
    void push(int x) {
        if(x < min_val)
        {
            min_val = x;
            stk.push({x,min_val});
        }
        else
            stk.push({x,min_val});
    }
    
    void pop() {
        if(!stk.empty())
            stk.pop();
        if(stk.empty())
            min_val = INT_MAX;
        else
            min_val = stk.top().second;
    }
    
    int top() {
        return stk.top().first;
    }
    
    int min() {
        return min_val;
    }
};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack* obj = new MinStack();
 * obj->push(x);
 * obj->pop();
 * int param_3 = obj->top();
 * int param_4 = obj->min();
 */
~~~


# <a name="53">53-I. 在排序数组中查找数字</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

统计一个数字在排序数组中出现的次数。

**示例1：**
~~~
输入: nums = [5,7,7,8,8,10], target = 8
输出: 2
~~~

**示例1：**
~~~
输入: nums = [5,7,7,8,8,10], target = 6
输出: 0
~~~

**限制：**
~~~
0 <= 数组长度 <= 50000
~~~

**解答1:**
~~~cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int res = 0;
        for(int i = 0;i<nums.size();i++)
        {
            if(nums[i] == target) res++;
        }
        return res;
    }
};
~~~

**解答2:**
~~~cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        if(nums.size() == 0)
            return 0;
        int l = first(nums, target);
        if (l == -1)
            return 0;
        int r = last(nums, target);
        return r - l + 1;
    }

    int first(vector<int>& nums, int target){
        int l = 0;
        int r = nums.size() - 1;
        while(l <= r){
            int mid = l + (r - l) / 2;
            if(nums[mid] == target)
                r = mid - 1;
            else if(nums[mid] > target)
                r = mid - 1;
            else  // nums[mid] < target
                l = mid + 1;
        }
        if(l >= nums.size() || nums[l] != target) // if(l == nums.size() || nums[r + 1] != target)
            return -1;
        return l;
    }

    int last(vector<int>& nums, int target){
        int l = 0;
        int r = nums.size() - 1;
        while(l <= r){
            int mid = l + (r - l) / 2;
            if(nums[mid] == target)
                l = mid + 1;
            else if(nums[mid] < target)
                l = mid + 1;
            else // nums[mid] > target
                r = mid - 1;
        }
        if(r < 0 || nums[l - 1] != target) // if(r == -1 || nums[r] != target)
            return -1;
        return r;
    }
};
~~~


# <a name="53-II">53-II. 0～n-1中缺失的数字</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

一个长度为n-1的递增排序数组中的所有数字都是唯一的，并且每个数字都在范围0～n-1之内。在范围0～n-1内的n个数字中有且只有一个数字不在该数组中，请找出这个数字。


**示例1：**
~~~
输入: [0,1,3]
输出: 2
~~~

**示例1：**
~~~
输入: [0,1,2,3,4,5,6,7,9]
输出: 8
~~~

**限制：**
~~~
1 <= 数组长度 <= 10000
~~~

**解答1:**
~~~cpp
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int left = 0, right = nums.size() - 1;
        while(left <= right)
        {
            int mid = (left + right) >> 1;
            if(nums[mid] == mid)
            {
                left = mid + 1;
            }
            else 
                right = mid - 1;
        }
        return left;
    }
};
~~~


# <a name="59">59.II. 队列的最大值</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

请定义一个队列并实现函数 max_value 得到队列里的最大值，要求函数max_value、push_back 和 pop_front 的均摊时间复杂度都是O(1)。

若队列为空，pop_front 和 max_value 需要返回 -1


**示例1：**
~~~
输入: 
["MaxQueue","push_back","push_back","max_value","pop_front","max_value"]
[[],[1],[2],[],[],[]]
输出: [null,null,null,2,1,2]
~~~

**示例1：**
~~~
输入: 
["MaxQueue","pop_front","max_value"]
[[],[],[]]
输出: [null,-1,-1]
~~~

**限制：**

* 1 <= push_back,pop_front,max_value的总操作数 <= 10000
* 1 <= value <= 10^5

**解答1:**
~~~cpp
class MaxQueue {
public:
    std::stack<int> stk1,stk2;
    int max_val,sup_val;
    MaxQueue() {
        max_val = INT_MIN;
        sup_val = INT_MIN;
    }
    
    int max_value() {
        if(stk1.empty())
            return -1;
        else return max_val;
    }
    
    void push_back(int value) {
        stk1.push(value);
        if(max_val < value)
            max_val = value;
    }
    
    int pop_front() {
        if(stk1.empty()) return -1;
        while(stk1.size() > 1)
        {
            stk2.push(stk1.top());
            if(sup_val < stk1.top()) sup_val = stk1.top();
            stk1.pop();
        }
        max_val = sup_val;
        sup_val = INT_MIN;
        int res = stk1.top();
        stk1.pop();
        while(!stk2.empty())
        {
            stk1.push(stk2.top());
            stk2.pop();
        }
        return res;
    }
};

/**
 * Your MaxQueue object will be instantiated and called as such:
 * MaxQueue* obj = new MaxQueue();
 * int param_1 = obj->max_value();
 * obj->push_back(value);
 * int param_3 = obj->pop_front();
 */
~~~
