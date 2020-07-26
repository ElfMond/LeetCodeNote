<a name="index">**Index**</a>  
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
<a href="#13">13. 机器人的运动范围</a>  
<a href="#14-I">14-I. 剪绳子</a>  
<a href="#15">15. 二进制中1的个数</a>  
<a href="#16">16. 数值的整数次方</a>  
<a href="#17">17. 打印从1到最大的n位数</a>  
<a href="#18">18. 删除链表的节点</a>  
<a href="#19">19. 正则表达式匹配</a>  
<a href="#20">20. 表示数值的字符串</a>  
<a href="#21">21. 调整数组顺序使奇数位于偶数前面</a>  
<a href="#22">22. 链表中倒数第k个节点</a>  
<a href="#24">24. 反转链表</a>  
<a href="#25">25. 合并两个排序的链表</a>  
<a href="#26">26. 树的子结构</a>  
<a href="#27">27. 二叉树的镜像</a>  
<a href="#28">28. 对称的二叉树</a>  
<a href="#29">29. 顺时针打印矩阵</a>  
<a href="#30">30. 包含min函数的栈</a>  
<a href="#31">31. 栈的压入、弹出序列</a>  
<a href="#32-I">32-I. 从上到下打印二叉树</a>  
<a href="#32-II">32-II. 从上到下打印二叉树 II</a>  
<a href="#32-III">32-III. 从上到下打印二叉树 III</a>  
<a href="#33">33. 二叉搜索树的后序遍历序列</a>  
<a href="#34">34. 二叉树中和为某一值的路径</a>  
<a href="#35">35. 复杂链表的复制</a>  
<a href="#36">36. 二叉搜索树与双向链表</a>  
<a href="#38">38. 字符串的排列</a>  
<a href="#39">39. 数组中出现次数超过一半的数字</a>  
<a href="#41">41. 数据流中的中位数</a>  
<a href="#42">42. 连续子数组的最大和</a>  
<a href="#43">43. 1～n整数中1出现的次数</a>  
<a href="#44">44. 数字序列中某一位的数字</a>  
<a href="#45">45. 把数组排成最小的数</a>  
<a href="#46">46. 把数字翻译成字符串</a>  
<a href="#47">47. 礼物的最大价值</a>  
<a href="#48">48. 最长不含重复字符的子字符串</a>  
<a href="#50">50. 第一个只出现一次的字符</a>  
<a href="#52">52. 两个链表的第一个公共节点</a>  
<a href="#53-I">53-I. 在排序数组中查找数字</a>  
<a href="#53-II">53-II. 0～n-1中缺失的数字</a>  
<a href="#54">54. 二叉搜索树的第k大节点</a>  
<a href="#55-I">55-I. 二叉树的深度</a>  
<a href="#55-II">55-II. 平衡二叉树</a>  
<a href="#56-I">56-I. 数组中数字出现的次数</a>  
<a href="#56-II">56-II. 数组中数字出现的次数 II</a>  
<a href="#57">57. 和为s的两个数字</a>  
<a href="#57-II">57-II. 和为s的连续正数序列</a>  
<a href="#58-I">58-I. 翻转单词顺序</a>  
<a href="#58-II">58-II. 左旋转字符串</a>  
<a href="#59-I">59-I. 滑动窗口的最大值</a>  
<a href="#59-II">59-II. 队列的最大值</a>  
<a href="#60">60. n个骰子的点数</a>  
<a href="#61">61. 扑克牌中的顺子</a>  
<a href="#62">62. 圆圈中最后剩下的数字</a>  
<a href="#63">63. 股票的最大利润</a>  
<a href="#64">64. 求1+2+…+n</a>  
<a href="#65">65. 不用加减乘除做加法</a>  
<a href="#66">66. 构建乘积数组</a>  
<a href="#68-I">68-I. 二叉搜索树的最近公共祖先</a>  
<a href="#68-II">68-II. 二叉树的最近公共祖先</a>  

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



# <a name="13">13. 机器人的运动范围</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

地上有一个m行n列的方格，从坐标 [0,0] 到坐标 [m-1,n-1] 。一个机器人从坐标 [0, 0] 的格子开始移动，它每次可以向左、右、上、下移动一格（不能移动到方格外），也不能进入行坐标和列坐标的数位之和大于k的格子。例如，当k为18时，机器人能够进入方格 [35, 37] ，因为3+5+3+7=18。但它不能进入方格 [35, 38]，因为3+5+3+8=19。请问该机器人能够到达多少个格子？


**示例1：**

~~~
输入：m = 2, n = 3, k = 1
输出：3
~~~

**示例2：**
~~~
输入：m = 3, n = 1, k = 0
输出：1
~~~

**提示：**

* 1 <= n,m <= 100
* 0 <= k <= 20

**解答1:**
~~~cpp
//BFS
class Solution {
public:
    int movingCount(int m, int n, int k) {
        int res = 0;
        std::vector<std::vector<int>> visited(m , std::vector<int>(n , 0));
        std::queue<std::pair<int,int>> Q;
        Q.push({0,0});
        visited[0][0] = 1;
        while(Q.size())
        {
            std::pair<int,int> curr = Q.front();
            Q.pop();
            res++;
            std::pair<int,int> right = {curr.first,curr.second + 1};
            std::pair<int,int> down = {curr.first + 1,curr.second};
            if(right.first < m && right.second < n && digsumvalid(right.first,right.second,k))
            {
                if(visited[right.first][right.second] == 0)
                {
                    Q.push(right);
                    visited[right.first][right.second] = 1;
                }
            }
            if(down.first < m && down.second < n && digsumvalid(down.first,down.second,k))
            {
                if(visited[down.first][down.second] == 0)
                {
                    Q.push(down);
                    visited[down.first][down.second] = 1;
                }
            }
        }
        return res;
    }
    bool digsumvalid(int m,int n,int k) 
    {
        return ((n % 10 + (n / 10) % 10 + (n / 100) % 10)+(m % 10 + (m / 10) % 10 + (m / 100) % 10)) <= k;
    }
};
~~~


# <a name="14-I">14-I. 剪绳子I</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

给你一根长度为 n 的绳子，请把绳子剪成整数长度的 m 段（m、n都是整数，n>1并且m>1），每段绳子的长度记为 `k[0],k[1]...k[m-1]` 。请问`k[0]*k[1]*...*k[m-1]`  可能的最大乘积是多少？例如，当绳子的长度是8时，我们把它剪成长度分别为2、3、3的三段，此时得到的最大乘积是18。


**示例1：**

例如，给出
~~~
输入: 2
输出: 1
解释: 2 = 1 + 1, 1 × 1 = 1
~~~

**示例2：**
~~~
输入: 10
输出: 36
解释: 10 = 3 + 3 + 4, 3 × 3 × 4 = 36
~~~


**解答1:**
~~~cpp
class Solution {
public:
    int cuttingRope(int n) {
        int* num = new int[n+1];
        *(num+1) = 1;
        for(int i = 2;i < n + 1;i++)
        {
            *(num + i) = *(num + i -1);
            for(int j = 1;j < i;j++)
            {
                
                if(j*(*(num + i - j)) > *(num + i)) 
                    *(num + i) = j*(*(num + i - j));
                if(((i-j)*j) > *(num + i)) 
                    *(num + i) = (i-j)*j;
            }
        }
        return *(num + n);
    }
};
~~~


# <a name="14-II">14-II. 剪绳子II</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

给你一根长度为 n 的绳子，请把绳子剪成整数长度的 m 段（m、n都是整数，n>1并且m>1），每段绳子的长度记为 `k[0],k[1]...k[m-1]` 。请问`k[0]*k[1]*...*k[m-1]`  可能的最大乘积是多少？例如，当绳子的长度是8时，我们把它剪成长度分别为2、3、3的三段，此时得到的最大乘积是18。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。


**示例1：**

例如，给出
~~~
输入: 2
输出: 1
解释: 2 = 1 + 1, 1 × 1 = 1
~~~

**示例2：**
~~~
输入: 10
输出: 36
解释: 10 = 3 + 3 + 4, 3 × 3 × 4 = 36
~~~


**解答1:**
~~~cpp

~~~


# <a name="15">15. 二进制中1的个数</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

请实现一个函数，输入一个整数，输出该数二进制表示中 1 的个数。例如，把 9 表示成二进制是 1001，有 2 位是 1。因此，如果输入 9，则该函数输出 2。


**示例1：**

例如，给出
~~~
输入：00000000000000000000000000001011
输出：3
解释：输入的二进制串 00000000000000000000000000001011 中，共有三位为 '1'。
~~~

**示例2：**
~~~
输入：00000000000000000000000010000000
输出：1
解释：输入的二进制串 00000000000000000000000010000000 中，共有一位为 '1'。
~~~

**示例3：**
~~~
输入：11111111111111111111111111111101
输出：31
解释：输入的二进制串 11111111111111111111111111111101 中，共有 31 位为 '1'。
~~~

**解答1:**
~~~cpp
class Solution {
public:
    int hammingWeight(uint32_t n) {
        int res = 0;
        while(n)
        {
            if(n&1) res++;
            n>>=1;
        }
        return res;
    }
};
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


# <a name="17">17. 打印从1到最大的n位数</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

输入数字 n，按顺序打印出从 1 到最大的 n 位十进制数。比如输入 3，则打印出 1、2、3 一直到最大的 3 位数 999。


**示例1：**

~~~
输入: n = 1
输出: [1,2,3,4,5,6,7,8,9]
~~~

**说明：**

* 用返回一个整数列表来代替打印
* n 为正整数

**解答1:**
~~~cpp
class Solution {
public:
    vector<int> printNumbers(int n) {
        int lim = 1;
        for(int i = 0;i < n;i++) lim *= 10;
        std::vector<int> res;
        for(int i = 0;i < lim-1;i++)
            res.push_back(i+1);
        return res;
    }
};
~~~


# <a name="18">18. 删除链表的节点</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

给定单向链表的头指针和一个要删除的节点的值，定义一个函数删除该节点。 返回删除后的链表的头节点。


**示例1：**

~~~
输入: head = [4,5,1,9], val = 5
输出: [4,1,9]
解释: 给定你链表中值为 5 的第二个节点，那么在调用了你的函数之后，该链表应变为 4 -> 1 -> 9.
~~~

**示例2：**
~~~
输入: head = [4,5,1,9], val = 1
输出: [4,5,9]
解释: 给定你链表中值为 1 的第三个节点，那么在调用了你的函数之后，该链表应变为 4 -> 5 -> 9.
~~~

**说明**
* 题目保证链表中节点的值互不相同
* 若使用 C 或 C++ 语言，你不需要 free 或 delete 被删除的节点

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
    ListNode* deleteNode(ListNode* head, int val) {
        if(head->val == val) return head->next;
        for(auto it = head;it != nullptr;it = it->next)
        {
            if(it->next->val == val)
            {
                it->next = it->next->next;
                break;
            }
        }
        return head;
    }
};
~~~


# <a name="19">19. 正则表达式匹配</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

请实现一个函数用来匹配包含'. '和'\*'的正则表达式。模式中的字符'.'表示任意一个字符，而'\*'表示它前面的字符可以出现任意次（含0次）。在本题中，匹配是指字符串的所有字符匹配整个模式。例如，字符串"aaa"与模式"a.a"和"ab\*ac\*a"匹配，但与"aa.a"和"ab\*a"均不匹配。

**示例1：**

~~~
输入:
s = "aa"
p = "a"
输出: false
解释: "a" 无法匹配 "aa" 整个字符串。
~~~

**示例2：**
~~~
输入:
s = "aa"
p = "a*"
输出: true
解释: 因为 '*' 代表可以匹配零个或多个前面的那一个元素, 在这里前面的元素就是 'a'。因此，字符串 "aa" 可被视为 'a' 重复了一次。
~~~

**示例3:**
~~~
输入:
s = "ab"
p = ".*"
输出: true
解释: ".*" 表示可匹配零个或多个（'*'）任意字符（'.'）。
~~~
**示例4:**
~~~
输入:
s = "aab"
p = "c*a*b"
输出: true
解释: 因为 '*' 表示零个或多个，这里 'c' 为 0 个, 'a' 被重复一次。因此可以匹配字符串 "aab"。
~~~
**示例5:**
~~~
输入:
s = "mississippi"
p = "mis*is*p*."
输出: false
~~~

**说明**
* s 可能为空，且只包含从 a-z 的小写字母。
* p 可能为空，且只包含从 a-z 的小写字母以及字符 . 和 \*，无连续的 ' \*'。
* 
**解答1:**
~~~cpp
class Solution {
public:
    bool isMatch(string s, string p) {
        if(p[0]=='\0')
        {
            if(s[0]=='\0') //递归出口
                return true;
            else
                return false;
        }
        if(p[1] == '*') //匹配*
        {
            if(isMatch(s,p.substr(2))) return true;
            if(s[0] != '\0' && (s[0] == p[0] || p[0] == '.') && isMatch(s.substr(1), p)) return true;
        }
        if(s[0] != '\0' && (s[0] == p[0] || p[0] == '.') && isMatch(s.substr(1), p.substr(1))) return true;
        else return false;
    }
};
~~~


# <a name="20">20. 表示数值的字符串</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

请实现一个函数用来判断字符串是否表示数值（包括整数和小数）。例如，字符串"+100"、"5e2"、"-123"、"3.1416"、"0123"都表示数值，但"12e"、"1a3.14"、"1.2.3"、"+-5"、"-1E-16"及"12e+5.4"都不是。


**解答1:**
~~~cpp
class Solution {
public:
    bool isNumber(string s) {
        if(deleteblank(s) == false) return false;
        if(deleteblankback(s) == false) return false;
        if(s.empty()) return false;
        if(deletesign(s) == false) return false;
        if(deletedig(s) == false) return false;
        if(s[0] == '\0') return true;
        if(deletee(s) == false) return false;
        if(deletesign(s) == false) return false;
        if(deleteintdig(s) == false) return false;
        return true;
    }
    bool deleteblank(string& s)
    {
        while(s[0] == ' ')
            s = s.substr(1,s.size() - 1);
        if(s.empty()) return false;
        return true;
    }
    bool deleteblankback(string& s)
    {
        while(s[s.size() - 1] == ' ')
            s = s.substr(0,s.size() - 1);
        if(s.empty()) return false;
        return true;
    }
    bool deletesign(string& s)
    {
        if(s[0] == '+' || s[0] == '-')
            s = s.substr(1,s.size() - 1);
        return (s[0] >= '0' && s[0] <= '9')|| s[0] == '.';
    }
    bool deletedig(string& s)
    {
        bool front = false;
        bool back = false;
        while(s[0] >= '0' && s[0] <= '9')
        {
            s = s.substr(1,s.size() - 1);
            front = true;
        }
        if(s[0] == '.') 
        {
            s = s.substr(1,s.size() - 1);
            if(!((s[0] >= '0' && s[0] <= '9') || s[0] == '\0' || s[0] == 'e')) return false;
            while(s[0] >= '0' && s[0] <= '9')
            {
                s = s.substr(1,s.size() - 1);
                back = true;
            }
            if(s[0] == 'e'||s[0] == '\0') return front|back;
            else return false;
        }
        if(s[0] == 'e'||s[0] == '\0') return true;
        else return false;
    }
    bool deletee(string& s)
    {
        if(s[0] == 'e')
            s = s.substr(1,s.size() - 1);
        return (s[0] == '+' || s[0] == '-' || (s[0] >= '0' && s[0] <= '9'));
    }
    bool deleteintdig(string& s)
    {
        while(s[0] >= '0' && s[0] <= '9')
        {
            s = s.substr(1,s.size() - 1);
        }
        if(s[0] == '\0') return true;
        else return false;
    }
};
~~~


# <a name="21">21. 调整数组顺序使奇数位于偶数前面</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有奇数位于数组的前半部分，所有偶数位于数组的后半部分。


**示例1：**

~~~
输入：nums = [1,2,3,4]
输出：[1,3,2,4] 
注：[3,1,2,4] 也是正确的答案之一。
~~~

**提示：**

* 1 <= nums.length <= 50000
* 1 <= nums[i] <= 10000

**解答1:**
~~~cpp
class Solution {
public:
    vector<int> exchange(vector<int>& nums) {
        /*
        for(int i = 0,j = 0;i < nums.size();i++)
        {
            if(!(nums[j]%2)) 
            {
                nums.push_back(nums[j]);
                nums.erase(nums.begin()+j);
                j--;
            }
            j++;
        }
        return nums;
        */
        if(nums.size()==0) return nums;
        auto left = nums.begin();
        auto right = nums.end()-1;
        while(left < right)
        {
            if(((*left)%2 == 0)&&((*right)%2 != 0)) std::swap(*left,*right);
            if((*left)%2 != 0) left += 1;
            if((*right)%2 == 0) right -= 1;
        }
        return nums;
    }
};
~~~


# <a name="22">22. 链表中倒数第k个节点</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

输入一个链表，输出该链表中倒数第k个节点。为了符合大多数人的习惯，本题从1开始计数，即链表的尾节点是倒数第1个节点。例如，一个链表有6个节点，从头节点开始，它们的值依次是1、2、3、4、5、6。这个链表的倒数第3个节点是值为4的节点。


**示例1：**

~~~
给定一个链表: 1->2->3->4->5, 和 k = 2.

返回链表 4->5.
~~~


**解答1:**
~~~cpp
//12ms
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
    ListNode* getKthFromEnd(ListNode* head, int k) {
        int num = 1;
        for(auto it = head;it != nullptr; it = it->next)
        {
            num++;
        }
        auto res = head;
        for(int i = 1;i < num - k;i++)
        {
            res = res->next;
        }
        return res;
    }
};
~~~

**解答2:**
~~~cpp
//8ms
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
    ListNode* getKthFromEnd(ListNode* head, int k) {
        ListNode* fast = head;
        for(int i = 0;i < k;i++) fast = fast->next;
        while(fast)
        {
            head = head->next;
            fast = fast->next;
        }
        return head;
    }
};
~~~

# <a name="24">24. 反转链表</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

定义一个函数，输入一个链表的头节点，反转该链表并输出反转后链表的头节点。


**示例1：**

~~~
输入: 1->2->3->4->5->NULL
输出: 5->4->3->2->1->NULL
~~~

**限制：**

0 <= 节点个数 <= 5000

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
    ListNode* reverseList(ListNode* head) {
        ListNode* pre = nullptr;
        while(head)
        {
            ListNode* nxt = head->next;
            head->next = pre;
            pre = head;
            head = nxt;
        }
        return pre;
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


# <a name="26">26. 树的子结构</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

输入两棵二叉树A和B，判断B是不是A的子结构。(约定空树不是任意一个树的子结构)

B是A的子结构， 即 A中有出现和B相同的结构和节点值。
~~~
例如:
给定的树 A:

     3
    / \
   4   5
  / \
 1   2
给定的树 B：

   4 
  /
 1
返回 true，因为 B 与 A 的一个子树拥有相同的结构和节点值。
~~~

**示例1：**

~~~
输入：A = [1,2,3], B = [3,1]
输出：false
~~~

**示例2: **
~~~
输入：A = [3,4,5,1,2], B = [4,1]
输出：true
~~~
限制：
~~~
0 <= 节点个数 <= 10000
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
    bool isSubStructure(TreeNode* A, TreeNode* B) {
        if(B == nullptr || A == nullptr) return false;
        std::queue<TreeNode*> Q;
        Q.push(A);
        while(Q.size())
        {
            TreeNode* currA = Q.front();
            if(currA->val == B->val) 
            {
                if(compare(currA, B))
                    return true;
            }
            Q.pop();
            if(currA->left != nullptr) Q.push(currA->left);
            if(currA->right != nullptr) Q.push(currA->right);
        }
        return false;
    }
    bool compare(TreeNode* A, TreeNode* B)
    {
        std::queue<TreeNode*> QB;
        std::queue<TreeNode*> QAA;
        QB.push(B);
        QAA.push(A);
        while(QB.size())
        {
            TreeNode* currB = QB.front();
            TreeNode* currA = QAA.front();
            if(currA->val != currB->val) return false;
            QB.pop();
            QAA.pop();
            if(currB->left != nullptr)
            {
                if(currA->left == nullptr)
                    return false;
                else
                    QB.push(currB->left);
                    QAA.push(currA->left);
            }
            if(currB->right != nullptr)
            {
                if(currA->right == nullptr)
                    return false;
                else
                    QB.push(currB->right);
                    QAA.push(currA->right);
            }
        }
        return true;
    }
};
~~~
**解答2:**
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
    bool isSubStructure(TreeNode* A, TreeNode* B) {
        if(B == nullptr || A == nullptr) return false;
        std::queue<TreeNode*> Q;
        Q.push(A);
        while(Q.size())
        {
            TreeNode* currA = Q.front();
            if(currA->val == B->val) 
            {
                if(compare(currA, B))
                    return true;
            }
            Q.pop();
            if(currA->left != nullptr) Q.push(currA->left);
            if(currA->right != nullptr) Q.push(currA->right);
        }
        return false;
    }
    bool compare(TreeNode* A, TreeNode* B)
    {
        if(B == nullptr) return true;
        if(A == nullptr) return false;
        if(A->val == B->val) return compare(A->left,B->left)&compare(A->right, B->right);
        return false;
    }
};
~~~


# <a name="27">27. 二叉树的镜像</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

请完成一个函数，输入一个二叉树，该函数输出它的镜像。
~~~
例如输入：
     4
   /   \
  2     7
 / \   / \
1   3 6   9
镜像输出：

     4
   /   \
  7     2
 / \   / \
9   6 3   1
~~~

**示例1：**

~~~
输入：root = [4,2,7,1,3,6,9]
输出：[4,7,2,9,6,3,1]
~~~

**限制：**
~~~
0 <= 节点个数 <= 1000
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
    TreeNode* mirrorTree(TreeNode* root) {
        TreeNode* res = root;
        rec(root);
        return res;
    }
    void rec(TreeNode* t)
        {
            if(t == nullptr) return;
            TreeNode* tmp = t->left;
            t->left = t->right;
            t->right = tmp;
            rec(t->left);
            rec(t->right);
        }
};
~~~



# <a name="28">28.  对称的二叉树</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

请实现一个函数，用来判断一棵二叉树是不是对称的。如果一棵二叉树和它的镜像一样，那么它是对称的。
~~~
例如，二叉树 [1,2,2,3,4,4,3] 是对称的。

    1
   / \
  2   2
 / \ / \
3  4 4  3
但是下面这个 [1,2,2,null,3,null,3] 则不是镜像对称的:

    1
   / \
  2   2
   \   \
   3    3
~~~

**示例1：**
~~~
输入：root = [1,2,2,3,4,4,3]
输出：true
~~~

**示例2：**
~~~
输入：root = [1,2,2,null,3,null,3]
输出：false
~~~

**限制：**
~~~
0 <= 节点个数 <= 1000
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
    bool isSymmetric(TreeNode* root) {
        if(root == nullptr) return true;
        return rec(root->left,root->right);
    }
    bool rec(TreeNode* left,TreeNode* right)
    {
        if(left == nullptr && right == nullptr) return true;
        if(left == nullptr || right == nullptr) return false;
        if(left->val != right->val) return false;
        return rec(left->left,right->right) && rec(left->right,right->left);
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


# <a name="31">31. 栈的压入、弹出序列</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

输入两个整数序列，第一个序列表示栈的压入顺序，请判断第二个序列是否为该栈的弹出顺序。假设压入栈的所有数字均不相等。例如，序列 {1,2,3,4,5} 是某栈的压栈序列，序列 {4,5,3,2,1} 是该压栈序列对应的一个弹出序列，但 {4,3,5,1,2} 就不可能是该压栈序列的弹出序列。

**示例1：**

~~~
输入：pushed = [1,2,3,4,5], popped = [4,5,3,2,1]
输出：true
解释：我们可以按以下顺序执行：
push(1), push(2), push(3), push(4), pop() -> 4,
push(5), pop() -> 5, pop() -> 3, pop() -> 2, pop() -> 1
~~~

**示例2：**
~~~
输入：pushed = [1,2,3,4,5], popped = [4,3,5,1,2]
输出：false
解释：1 不能在 2 之前弹出。
~~~

**解答1:**
~~~cpp
//模拟栈混洗
class Solution {
public:
    bool validateStackSequences(vector<int>& pushed, vector<int>& popped) {
        if(pushed.empty()) return true;
        std::stack<int> B;
        int p = 0;
        for(int idx = 0;idx < popped.size();idx++)
        {
            if(p == pushed.size()  && B.top() != popped[idx]) return false;
            while((B.empty() || B.top() != popped[idx]) && (p < pushed.size()))
            {
                B.push(pushed[p++]);
            }
            B.pop();
        }
        return true;
    }
};
~~~


# <a name="32-I">32-I. 从上到下打印二叉树</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

从上到下按层打印二叉树，同一层的节点按从左到右的顺序打印，每一层打印到一行。

~~~
例如:
给定二叉树: [3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7
返回其层次遍历结果：
[3,9,20,15,7]
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
    vector<int> levelOrder(TreeNode* root) {
        std::queue<TreeNode*> Q;
        std::vector<int> res;
        if(root == nullptr) return res;
        Q.push(root);
        while(Q.size())
        {
            res.push_back(Q.front()->val);
            if(Q.front()->left) Q.push(Q.front()->left);
            if(Q.front()->right) Q.push(Q.front()->right);
            Q.pop();
        }
        return res;
    }
};
~~~




# <a name="32-II">32-II. 从上到下打印二叉树 II</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

从上到下按层打印二叉树，同一层的节点按从左到右的顺序打印，每一层打印到一行。

~~~
例如:
给定二叉树: [3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7
返回其层次遍历结果：

[
  [3],
  [9,20],
  [15,7]
]
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
    vector<vector<int>> levelOrder(TreeNode* root) {
        std::vector<std::vector<int>> res;
        if(root == nullptr) return res;
        std::queue<TreeNode*> Q;
        Q.push(root);
        while(!Q.empty())
        {
            int len = Q.size();
            std::vector<int> subres;
            for(int i = 0;i < len;i++)
            {
                auto front = Q.front();
                Q.pop();
                if(front->left) Q.push(front->left);
                if(front->right) Q.push(front->right);
                subres.push_back(front->val);
            }
            res.push_back(subres);
        }
        return res;
    }
};
~~~



# <a name="32-III">32-III. 从上到下打印二叉树 III</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

请实现一个函数按照之字形顺序打印二叉树，即第一行按照从左到右的顺序打印，第二层按照从右到左的顺序打印，第三行再按照从左到右的顺序打印，其他行以此类推。

~~~
例如:
给定二叉树: [3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7
返回其层次遍历结果：
[
  [3],
  [20,9],
  [15,7]
]
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
    vector<vector<int>> levelOrder(TreeNode* root) {
        std::vector<std::vector<int>> res;
        std::queue<TreeNode*> Q;
        if(root == nullptr) return res;
        Q.push(root);
        int len = Q.size();
        bool l = true;
        while(len)
        {
            std::vector<int> subres;
            for(int i = 0;i < len;i++)
            {
                subres.push_back(Q.front()->val);
                if(Q.front()->left) Q.push(Q.front()->left);
                if(Q.front()->right) Q.push(Q.front()->right);
                Q.pop();
            }
            len = Q.size();
            if(!l) std::reverse(subres.begin(),subres.end());
            res.push_back(subres);
            l = !l;
        }
        return res;
    }
};
~~~



# <a name="33">33. 二叉搜索树的后序遍历序列</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

输入一个整数数组，判断该数组是不是某二叉搜索树的后序遍历结果。如果是则返回 true，否则返回 false。假设输入的数组的任意两个数字都互不相同。

 
~~~
参考以下这颗二叉搜索树：

     5
    / \
   2   6
  / \
 1   3
~~~

**示例1：**

~~~
输入: [1,6,3,2,5]
输出: false
~~~
**示例2：**

~~~
输入: [1,3,2,6,5]
输出: true
~~~


**解答1:**
~~~cpp
class Solution {
public:
    bool verifyPostorder(vector<int>& postorder) {
        if(postorder.size() < 3) return true;
        int mid = postorder[postorder.size() - 1];
        auto idx_left = postorder.begin();
        while(idx_left < postorder.end() && *idx_left < mid) idx_left++;
        auto idx_right = idx_left;
        while(idx_right < postorder.end() - 1)
        {
            if(*idx_right < mid) return false;
            idx_right++;
        }
        std::vector<int> a(postorder.begin(),idx_left);
        std::vector<int> b(idx_left,postorder.end() - 1);
        return (verifyPostorder(a))&(verifyPostorder(b));
    }
};
~~~

# <a name="34">34. 二叉树中和为某一值的路径</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

输入一棵二叉树和一个整数，打印出二叉树中节点值的和为输入整数的所有路径。从树的根节点开始往下一直到叶节点所经过的节点形成一条路径。

**示例:**

给定如下二叉树，以及目标和 sum = 22，
~~~
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \    / \
        7    2  5   1
~~~
返回:
~~~
[
   [5,4,11,2],
   [5,8,4,5]
]
~~~

**提示：**

节点总数 <= 10000


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
    std::vector<std::vector<int>> res;
    vector<vector<int>> pathSum(TreeNode* root, int sum) {
        if(root == nullptr) return res;
        std::vector<int> subres;
        findpath(root,sum,subres);
        return res;
    }
    void findpath(TreeNode* root,int sum,std::vector<int>& subres)
    {
        if(root == nullptr) return;
        subres.emplace_back(root->val);
        if(root->val == sum && root->left == nullptr && root->right == nullptr) 
        {
            res.emplace_back(subres);
        }
        findpath(root->left,sum-root->val,subres);
        findpath(root->right,sum-root->val,subres);
        subres.pop_back();
    }
};
~~~



# <a name="35">35. 复杂链表的复制</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

请实现 copyRandomList 函数，复制一个复杂链表。在复杂链表中，每个节点除了有一个 next 指针指向下一个节点，还有一个 random 指针指向链表中的任意节点或者 null。

**示例1：**

![eg1](/img/35_1.png)
~~~
输入：head = [[7,null],[13,0],[11,4],[10,2],[1,0]]
输出：[[7,null],[13,0],[11,4],[10,2],[1,0]]
~~~
**示例2：**

![eg2](/img/35_2.png)
~~~
输入：head = [[1,1],[2,1]]
输出：[[1,1],[2,1]]
~~~
**示例3：**

![eg3](/img/35_3.png)
~~~
输入：head = [[3,null],[3,0],[3,null]]
输出：[[3,null],[3,0],[3,null]]
~~~
**示例3：**

~~~
输入：head = []
输出：[]
解释：给定的链表为空（空指针），因此返回 null。
~~~

**解答1:**
~~~cpp
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* next;
    Node* random;
    
    Node(int _val) {
        val = _val;
        next = NULL;
        random = NULL;
    }
};
*/
class Solution {
public:
    Node* copyRandomList(Node* head) {
        if(!head) return head;
        Node* ori = head;
        std::unordered_map<Node*,int> map1;
        std::unordered_map<int,Node*> map2;
        std::vector<int> relation;
        int idx = 0;
        map1[ori] = idx;
        Node* resNode = new Node(ori->val);
        Node* n = resNode;
        map2[idx] = n;
        ori = ori->next;
        while(ori)
        {
            idx++;
            map1[ori] = idx;
            n->next = new Node(ori->val);
            n = n->next;
            map2[idx] = n;
            ori = ori->next;
        }
        Node* ori2 = head;
        while(ori2)
        {
            if(ori2->random == nullptr) 
                relation.push_back(-1);
            else 
                relation.push_back(map1[ori2->random]);
            ori2 = ori2->next;
        }
        int idx_c = 0;
        Node* n2 = resNode;
        while(n2)
        {
            if(relation[idx_c] == -1) n2->random = nullptr;
            else n2->random = map2[relation[idx_c]];
            n2 = n2->next;
            idx_c++;
        }
        return resNode;
    }
};
~~~



# <a name="36">36. 二叉搜索树与双向链表</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

输入一棵二叉搜索树，将该二叉搜索树转换成一个排序的循环双向链表。要求不能创建任何新的节点，只能调整树中节点指针的指向。

为了让您更好地理解问题，以下面的二叉搜索树为例：


![eg](/img/36_1.png)
我们希望将这个二叉搜索树转化为双向循环链表。链表中的每个节点都有一个前驱和后继指针。对于双向循环链表，第一个节点的前驱是最后一个节点，最后一个节点的后继是第一个节点。

下图展示了上面的二叉搜索树转化成的链表。“head” 表示指向链表中有最小元素的节点。

![eg](/img/36_2.png)

特别地，我们希望可以就地完成转换操作。当转化完成以后，树中节点的左指针需要指向前驱，树中节点的右指针需要指向后继。还需要返回链表中的第一个节点的指针。

**解答1:**
~~~cpp
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* left;
    Node* right;

    Node() {}

    Node(int _val) {
        val = _val;
        left = NULL;
        right = NULL;
    }

    Node(int _val, Node* _left, Node* _right) {
        val = _val;
        left = _left;
        right = _right;
    }
};
*/
class Solution {
public:
    Node* treeToDoublyList(Node* root) {
        if(root == nullptr) return root;
        std::stack<Node*> S;
        Node* curr = root;
        std::vector<Node*> v;
        while(S.size() || curr != nullptr)
        {
            if(curr != nullptr)
            {
                S.push(curr);
                curr = curr->left;
            }
            else
            {
                Node* top = S.top();
                v.emplace_back(top);
                S.pop();
                curr = top->right;
            }
        }
        for(int i = 0;i < v.size() - 1;i++)
        {
            v[i]->right = v[i+1];
            v[i+1]->left = v[i];
        }
        v[v.size()-1]->right = v[0];
        v[0]->left = v[v.size()-1];
        return v[0];
    }
};
~~~


# <a name="38">38. 字符串的排列</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

输入一个字符串，打印出该字符串中字符的所有排列。

你可以以任意顺序返回这个字符串数组，但里面不能有重复元素。

**示例:**
~~~
输入：s = "abc"
输出：["abc","acb","bac","bca","cab","cba"]
~~~

**解答1:**
~~~cpp
class Solution {
public:
	std::vector<std::string> res;
	std::string s;
    vector<string> permutation(string c) {
        s = c;
        perm(0);
        return res;
    }
    void perm(int x)
	{
        if (x == s.size() - 1) res.push_back(s);
        std::unordered_map<char,int> charset;
        for (int i = x; i < s.size(); i++)
        {
            if (charset.find(s[i]) != charset.end()) continue;
            charset[s[i]] = i;
            char tmp = s[i];
            s[i] = s[x];
            s[x] = tmp;
            perm(x + 1);
            s[x] = s[i];
            s[i] = tmp;
        }
	}
};
~~~


# <a name="39">39. 数组中出现次数超过一半的数字</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。

你可以假设数组是非空的，并且给定的数组总是存在多数元素。


**示例1：**

~~~
输入: [1, 2, 3, 2, 2, 2, 5, 4, 2]
输出: 2
~~~

**限制：**

1 <= 数组长度 <= 50000

**解答1:**
~~~cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        std::unordered_map<int,int> mymap;
        int len = nums.size();
        int half = len >> 1;
        for(int i = 0;i < len;i++)
        {
            mymap[nums[i]]++;
            if(mymap[nums[i]] > half)
                return nums[i];
        }
        return nums[0];
    }
};
~~~



# <a name="41">41. 数据流中的中位数</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

如何得到一个数据流中的中位数？如果从数据流中读出奇数个数值，那么中位数就是所有数值排序之后位于中间的数值。如果从数据流中读出偶数个数值，那么中位数就是所有数值排序之后中间两个数的平均值。

例如，

[2,3,4] 的中位数是 3

[2,3] 的中位数是 (2 + 3) / 2 = 2.5

设计一个支持以下两种操作的数据结构：

void addNum(int num) - 从数据流中添加一个整数到数据结构中。
double findMedian() - 返回目前所有元素的中位数。

**示例1：**

~~~
输入：
["MedianFinder","addNum","addNum","findMedian","addNum","findMedian"]
[[],[1],[2],[],[3],[]]
输出：[null,null,null,1.50000,null,2.00000]
~~~
**示例2：**
~~~
输入：
["MedianFinder","addNum","findMedian","addNum","findMedian"]
[[],[2],[],[3],[]]
输出：[null,null,2.00000,null,2.50000]
~~~


**限制：**

最多会对 addNum、findMedia进行 50000 次调用。

**解答1:**
~~~cpp
class MedianFinder {
public:
    /** initialize your data structure here. */
    std::vector<int> nums;
    double median;
    MedianFinder() {
        std::vector<int> nums;
        double median = 0;
    }
    
    void addNum(int num) {
        int len = nums.size();
        if(len == 0) 
        {
            nums.push_back(num);
            median = num;
        }
        else
        {
            for(int i = 0;i<len;i++)
            {
                if(num <= nums[i]) 
                {
                    nums.insert(nums.begin()+i,num);
                    break;
                }
            }
            if(len == nums.size()) nums.insert(nums.end(),num);
            len++;
            if(len%2 == 0) 
                median = (nums[len/2 -1]+nums[len/2])/2.0;
            else 
                median = nums[(len+1)/2 -1];
        }
    }
    
    double findMedian() {
        return median;
    }
};

/**
 * Your MedianFinder object will be instantiated and called as such:
 * MedianFinder* obj = new MedianFinder();
 * obj->addNum(num);
 * double param_2 = obj->findMedian();
 */
~~~


# <a name="42">42. 连续子数组的最大和</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

输入一个整型数组，数组里有正数也有负数。数组中的一个或连续多个整数组成一个子数组。求所有子数组的和的最大值。

要求时间复杂度为O(n)。

**示例1：**

~~~
输入: nums = [-2,1,-3,4,-1,2,1,-5,4]
输出: 6
解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。
~~~

**提示：**

* 1 <= arr.length <= 10^5
* -100 <= arr[i] <= 100

**解答1:**
~~~cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int max = nums[0];
        int tmp = nums[0];
        for(int i = 1;i<nums.size();i++)
        {
            if(tmp < 0)
            {
                tmp = nums[i];
            }
            else tmp += nums[i];
            if(max < tmp) max = tmp;
        }
        return max;
    }
};
~~~



# <a name="43">43. 1～n整数中1出现的次数</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

输入一个整数 n ，求1～n这n个整数的十进制表示中1出现的次数。

例如，输入12，1～12这些整数中包含1 的数字有1、10、11和12，1一共出现了5次。



**示例1：**

~~~
输入：n = 12
输出：5
~~~

**示例2：**

~~~
输入：n = 13
输出：6
~~~

**限制：**

1 <= n < 2^31

**解答1:**
~~~cpp
class Solution {
public:
    int countDigitOne(int n) {
        int high = n/10;
        int curr = n%10;
        int low = 0;
        long dig = 1;
        int res = 0;
        while(high != 0 || curr != 0)
        {
            if(curr == 0) res += high*dig;
            else if(curr == 1) res += high*dig + low + 1;
            else if(curr > 1) res += high*dig + dig;
            dig *= 10;
            high = high/10;
            low = n%dig;
            curr = (n/dig)%10;
        }
        return res;
    }
};
~~~


# <a name="44">44. 数字序列中某一位的数字</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

数字以0123456789101112131415…的格式序列化到一个字符序列中。在这个序列中，第5位（从下标0开始计数）是5，第13位是1，第19位是4，等等。

请写一个函数，求任意第n位对应的数字。


**示例1：**

~~~
输入：n = 3
输出：3
~~~

**示例2：**

~~~
输入：n = 11
输出：0
~~~

**限制：**

1 <= n < 2^31

**解答1:**
~~~cpp
class Solution {
public:
    int findNthDigit(int n) {
        if(n < 10) return n;
        n = n - 10;
        int stage = 2;
        long num = 90;
        long cap = num*stage;
        while(n > cap)
        {
            n -= cap;
            stage++;
            num *= 10;
            cap = num*stage;
        }
        int first_num = 1;
        for(int i = 1;i<stage;i++) first_num *= 10;
        int numofdig = n/stage;
        int inthis = first_num + numofdig;
        int posindig = n%stage;
        for(int j = 0;j<posindig;j++) first_num /= 10;
        return (inthis/first_num)%10;
    }
};
~~~


# <a name="45">45. 把数组排成最小的数</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

输入一个非负整数数组，把数组里所有数字拼接起来排成一个数，打印能拼接出的所有数字中最小的一个。


**示例1：**

~~~
输入: [10,2]
输出: "102"
~~~

**示例2：**

~~~
输入: [3,30,34,5,9]
输出: "3033459"
~~~

**限制：**

0 < nums.length <= 100

**解答1:**
~~~cpp
class Solution {
public:
    string minNumber(vector<int>& nums) {
        std::sort(nums.begin(),nums.end(),compare);
        std::string res;
        for(int num : nums)
        {
            res += std::to_string(num);
        }
        return res;
    }
    static bool compare(const int& a,const int& b)
    {
        return std::to_string(a)+std::to_string(b)<std::to_string(b)+std::to_string(a);
    }
};
~~~


# <a name="46">46. 把数字翻译成字符串</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

给定一个数字，我们按照如下规则把它翻译为字符串：0 翻译成 “a” ，1 翻译成 “b”，……，11 翻译成 “l”，……，25 翻译成 “z”。一个数字可能有多个翻译。请编程实现一个函数，用来计算一个数字有多少种不同的翻译方法。



**示例1：**

~~~
输入: 12258
输出: 5
解释: 12258有5种不同的翻译，分别是"bccfi", "bwfi", "bczi", "mcfi"和"mzi"
~~~

**限制：**

0 <= num < 231

**解答1:**
~~~cpp
class Solution {
public:
    int translateNum(int num) {
        std::vector<int> numvec;
        while(num)
        {
            numvec.insert(numvec.begin(),num%10);
            num /= 10;
        }
        int prepre = 1;
        int pre = 1;
        for(int i = 1;i < numvec.size();i++)
        {
            if(10*numvec[i-1]+numvec[i] < 26 && numvec[i-1] != 0) 
            {
                int tmp = pre;
                pre = prepre + pre;
                prepre = tmp;
            }
            else
            {
                pre = pre;
                prepre = pre;
            }
        }
        return pre;
    }
};
~~~

**解答2:**
~~~cpp
class Solution {
public:
    int translateNum(int num) {
        int prenum = num%10;
        int prepre = 1;
        int pre = 1;
        while(num)
        {
            num /= 10;
            int currnum = num % 10;
            if(10*currnum+prenum < 26 && currnum != 0) 
            {
                int tmp = pre;
                pre = prepre + pre;
                prepre = tmp;
            }
            else
            {
                pre = pre;
                prepre = pre;
            }
            prenum = currnum;
        }
        return pre;
    }
};
~~~


# <a name="47">47. 礼物的最大价值</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

在一个 m*n 的棋盘的每一格都放有一个礼物，每个礼物都有一定的价值（价值大于 0）。你可以从棋盘的左上角开始拿格子里的礼物，并每次向右或者向下移动一格、直到到达棋盘的右下角。给定一个棋盘及其上面的礼物的价值，请计算你最多能拿到多少价值的礼物？

**示例1：**

~~~
输入: 
[
  [1,3,1],
  [1,5,1],
  [4,2,1]
]
输出: 12
解释: 路径 1→3→5→2→1 可以拿到最多价值的礼物
~~~

**提示：**

* 0 < grid.length <= 200
* 0 < grid[0].length <= 200

**解答1:**
~~~cpp
class Solution {
public:
    int maxValue(vector<vector<int>>& grid) {
        int m = grid.size();
        int n = grid[0].size();
        for(int i = 1;i < m;i++) grid[i][0] = grid[i-1][0] + grid[i][0];
        for(int j = 1;j < n;j++) grid[0][j] = grid[0][j-1] + grid[0][j];
        for(int i = 1;i < m;i++)
        {
            for(int j = 1;j < n;j++)
            {
                int pre = grid[i-1][j] < grid[i][j-1]? grid[i][j-1] : grid[i-1][j];
                grid[i][j] += pre;
            }
        }
        return grid[m-1][n-1];
    }
};
~~~




# <a name="48">48. 最长不含重复字符的子字符串</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

请从字符串中找出一个最长的不包含重复字符的子字符串，计算该最长子字符串的长度。

**示例1：**

~~~
输入: "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
~~~


**示例2：**

~~~
输入: "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
~~~

**示例3：**

~~~
输入: "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。
~~~


**提示**

* s.length <= 40000


**解答1:**
~~~cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        if(s.empty()) return 0;
        std::unordered_map<char, int> slidewindow = {{s[0],0}};
        int left = 0, right = 0, maxlength = 1;
        while(++right < s.size())
        {
            if(slidewindow.find(s[right]) == slidewindow.end())
            {
                slidewindow[s[right]] = right;
                maxlength = maxlength < (right - left + 1)? right - left + 1 : maxlength;
            }
            else
            {
                while(slidewindow.find(s[right]) != slidewindow.end())
                {
                    slidewindow.erase(s[left]);
                    left++;
                }
                slidewindow[s[right]] = right;
            }
        }
        return maxlength;
    }
};
~~~

**解答2:**
~~~cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int max_length = 0;
        int front = -1;
        std::vector<int> dict (256, -1);
        for(int i = 0; i != s.length(); i++){
            if(dict[s[i]] > front) 
                front = dict[s[i]];
            dict[s[i]] = i;
            max_length = max(max_length, i - front);
        }
        return max_length;
    }
};
~~~


# <a name="50">50. 第一个只出现一次的字符</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

在字符串 s 中找出第一个只出现一次的字符。如果没有，返回一个单空格。 s 只包含小写字母。

**示例：**

~~~
s = "abaccdeff"
返回 "b"

s = "" 
返回 " "
~~~


**限制**

* 0 <= s 的长度 <= 50000


**解答1:**
~~~cpp
//96ms
class Solution {
public:
    char firstUniqChar(string s) {
        if(s.empty()) return ' ';
        std::unordered_map<char,int> mymap;
        for(int i = 0;i < s.size();i++)
        {
            mymap[s[i]]++;
        }
        for(int i = 0;i < s.size();i++) 
        {
            if(mymap[s[i]] == 1)
            {
                return s[i];
            }
        }
        return ' ';
    }
};
~~~

**解答2:**
~~~cpp
//32ms
class Solution {
public:
    char firstUniqChar(string s) {
        if(s.empty()) return ' ';
        int count[26] = {0};
        for(int i = 0;i < s.size();i++)
        {
            int b = s[i] -'a';
            count[b]++;
        }
        for(int i = 0;i < s.size();i++) 
        {
            int b = s[i] -'a';
            if(count[b] == 1)
            {
                return s[i];
            }
        }
        return ' ';
    }
};
~~~

# <a name="52">52. 两个链表的第一个公共节点</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

在字符串 s 中找出第一个只出现一次的字符。如果没有，返回一个单空格。 s 只包含小写字母。

**示例1：**

![eg1](img/52_1.png)
~~~
输入：intersectVal = 8, listA = [4,1,8,4,5], listB = [5,0,1,8,4,5], skipA = 2, skipB = 3
输出：Reference of the node with value = 8
输入解释：相交节点的值为 8 （注意，如果两个列表相交则不能为 0）。从各自的表头开始算起，链表 A 为 [4,1,8,4,5]，链表 B 为 [5,0,1,8,4,5]。在 A 中，相交节点前有 2 个节点；在 B 中，相交节点前有 3 个节点。
~~~

![eg2](img/52_2.png)
~~~
输入：intersectVal = 2, listA = [0,9,1,2,4], listB = [3,2,4], skipA = 3, skipB = 1
输出：Reference of the node with value = 2
输入解释：相交节点的值为 2 （注意，如果两个列表相交则不能为 0）。从各自的表头开始算起，链表 A 为 [0,9,1,2,4]，链表 B 为 [3,2,4]。在 A 中，相交节点前有 3 个节点；在 B 中，相交节点前有 1 个节点。
~~~


![eg3](img/52_3.png)
~~~
输入：intersectVal = 0, listA = [2,6,4], listB = [1,5], skipA = 3, skipB = 2
输出：null
输入解释：从各自的表头开始算起，链表 A 为 [2,6,4]，链表 B 为 [1,5]。由于这两个链表不相交，所以 intersectVal 必须为 0，而 skipA 和 skipB 可以是任意值。
解释：这两个链表不相交，因此返回 null。
~~~

**注意：**

* 如果两个链表没有交点，返回 null.
* 在返回结果后，两个链表仍须保持原有的结构。
* 可假定整个链表结构中没有循环。
* 程序尽量满足 O(n) 时间复杂度，且仅用 O(1) 内存。
* 本题与主站 160 题相同：https://leetcode-cn.com/problems/intersection-of-two-linked-lists/



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
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        ListNode* a = headA;
        std::unordered_map<ListNode*,int> mymap;
        while(a)
        {
            mymap[a] = 0;
            a = a->next;
        }
        ListNode* b = headB;
        while(b)
        {
            if(mymap.find(b)!=mymap.end()) return b;
            b = b->next;
        }
        return nullptr;
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
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        ListNode* a = headA;
        ListNode* b = headB;
        while(a!=b)
        {
            a = a != nullptr? a->next : headB;
            b = b != nullptr? b->next : headA;
        }
        return a;
    }
};
~~~



# <a name="53-I">53-I. 在排序数组中查找数字</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

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


# <a name="54">54. 二叉搜索树的第k大节点</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

给定一棵二叉搜索树，请找出其中第k大的节点。


**示例1：**
~~~
输入: root = [3,1,4,null,2], k = 1
   3
  / \
 1   4
  \
   2
输出: 4
~~~

**示例2：**
~~~
输入: root = [5,3,6,2,4,null,null,1], k = 3
       5
      / \
     3   6
    / \
   2   4
  /
 1
输出: 4
~~~

**限制：**
~~~
1 ≤ k ≤ 二叉搜索树元素个数
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
    int kthLargest(TreeNode* root, int k) {
        std::stack<TreeNode*> stk;
        TreeNode* curr = root;
        while(curr || stk.size())
        {
            while(curr)
            {
                stk.push(curr);
                curr = curr->right;
            }
            curr = stk.top();
            stk.pop();
            if(--k==0) return curr->val;
            curr = curr->left;
        }
        return 0;
    }
};
~~~


# <a name="55-I">55-I. 二叉树的深度</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

输入一棵二叉树的根节点，求该树的深度。从根节点到叶节点依次经过的节点（含根、叶节点）形成树的一条路径，最长路径的长度为树的深度。

例如：
~~~
给定二叉树 [3,9,20,null,null,15,7]，

    3
   / \
  9  20
    /  \
   15   7
返回它的最大深度 3 。
~~~

**限制：**
~~~
节点总数 <= 10000
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
    int maxDepth(TreeNode* root) {
        int res = 0;
        if(root == nullptr) return res;
        std::queue<TreeNode*> Q;
        Q.push(root);
        while(!Q.empty())
        {
            int len = Q.size();
            for(int i = 0;i < len;i++)
            {
                TreeNode* front = Q.front();
                Q.pop();
                if(front->left) Q.push(front->left);
                if(front->right) Q.push(front->right);
            }
            res++;
        }
        return res;
    }
};
~~~


# <a name="55-II">55-II. 平衡二叉树</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

输入一棵二叉树的根节点，判断该树是不是平衡二叉树。如果某二叉树中任意节点的左右子树的深度相差不超过1，那么它就是一棵平衡二叉树。

 

**示例 1:**
~~~
给定二叉树 [3,9,20,null,null,15,7]

    3
   / \
  9  20
    /  \
   15   7
返回 true 。
~~~
**示例 2:**
~~~
给定二叉树 [1,2,2,3,3,null,null,4,4]

       1
      / \
     2   2
    / \
   3   3
  / \
 4   4
返回 false 。
~~~

**限制：**
~~~
1 <= 树的结点个数 <= 10000
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
    bool isBalanced(TreeNode* root) {
        if(root==nullptr) return true;
        if(abs(maxDepth(root->left) - maxDepth(root->right)) > 1) return false;
        return(isBalanced(root->left)&&isBalanced(root->right));
    }

    int maxDepth(TreeNode* root) {
        int res = 0;
        if(root == nullptr) return res;
        std::queue<TreeNode*> Q;
        Q.push(root);
        while(!Q.empty())
        {
            int len = Q.size();
            for(int i = 0;i < len;i++)
            {
                TreeNode* front = Q.front();
                Q.pop();
                if(front->left) Q.push(front->left);
                if(front->right) Q.push(front->right);
            }
            res++;
        }
        return res;
    }
};
~~~


# <a name="56-I">56-I. 数组中数字出现的次数</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

一个整型数组 nums 里除两个数字之外，其他数字都出现了两次。请写程序找出这两个只出现一次的数字。要求时间复杂度是O(n)，空间复杂度是O(1)。

 

**示例 1:**
~~~
输入：nums = [4,1,4,6]
输出：[1,6] 或 [6,1]
~~~
**示例 2:**
~~~
输入：nums = [1,2,10,4,1,4,3,3]
输出：[2,10] 或 [10,2]
~~~

**限制：**
~~~
2 <= nums.length <= 10000
~~~

**解答1:**
~~~cpp
class Solution {
public:
    vector<int> singleNumbers(vector<int>& nums) {
        std::vector<int> res;
        std::unordered_map<int, int> mymap;
        for(int num:nums) mymap[num]++;
        for(auto p:mymap) 
            if(p.second == 1) res.push_back(p.first);
        return res;
    }
};
~~~

**解答2:**
~~~cpp
class Solution {
public:
    vector<int> singleNumbers(vector<int>& nums) {
        int ab = 0;
        int a = 0;
        int b = 0;
        for(int num : nums) ab ^= num;
        int div = 1;
        while((div&ab) == 0) div<<=1;
        for(int num :nums) 
        {
            if(num&div) a ^= num;
            else b ^= num;
        }
        return {a,b};
    }
};
~~~


# <a name="56-II">56-II. 数组中数字出现的次数 II</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

在一个数组 nums 中除一个数字只出现一次之外，其他数字都出现了三次。请找出那个只出现一次的数字。


**示例 1:**
~~~
输入：nums = [3,4,3,3]
输出：4
~~~
**示例 2:**
~~~
输入：nums = [9,1,7,9,7,9,7]
输出：1
~~~

**限制：**
~~~
1 <= nums.length <= 10000
1 <= nums[i] < 2^31
~~~

**解答1:**
~~~cpp
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int res;
        std::unordered_map<int, int> mymap;
        for(int num:nums) mymap[num]++;
        for(auto p:mymap) 
            if(p.second == 1) res = p.first;
        return res;
    }
};
~~~

**解答2:**
~~~cpp
/*  
            ab    ab    ab    ab
    状态机: 00 -> 01 -> 10 -> 00
    真值表:
    c   b   a   b'
    0   0   1   0
    0   0   0   0
    0   1   1   0
    0   1   0   1
    1   0   1   0
    1   0   0   1
    1   1   1   0
    1   1   0   0
    取结果为1的情况：b' = ~ab~c + ~a~bc = ~a(b~c+~bc) = ~a(b^c)
    因此，可以推出: b = b ^ c & ~a

    在更新b之后：
            ab    ab    ab    ab
    状态机: 01 -> 00 -> 10 -> 01
    调换ab: ba    ba    ba    ba
    状态机: 10 -> 00 -> 01 -> 10
    与上述一致，因此，可以推出：a = a ^ c & ~b
*/
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int a = 0, b = 0;
        for (int c: nums) {
            b = b ^ c & ~a;
            a = a ^ c & ~b;
        }
        return b;
    }
};
~~~


# <a name="57">57. 和为s的两个数字</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

输入一个**递增排序**的数组和一个数字s，在数组中查找两个数，使得它们的和正好是s。如果有多对数字的和等于s，则输出任意一对即可。

**示例 1:**
~~~
输入：nums = [2,7,11,15], target = 9
输出：[2,7] 或者 [7,2]
~~~
**示例 2:**
~~~
输入：nums = [10,26,30,31,47,60], target = 40
输出：[10,30] 或者 [30,10]
~~~

**限制：**

* 1 <= nums.length <= 10^5
* 1 <= nums[i] <= 10^6

**解答1:**
~~~cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        std::vector<int> res;
        std::unordered_map<int,int> mymap;
        for(int i = 0;i < nums.size();i++)
        {
            if(mymap.find(nums[i]) != mymap.end())
            {
                res.push_back(nums[mymap[nums[i]]]);
                res.push_back(nums[i]);
                return res;
            }
            else
            {
                mymap[target - nums[i]] = i;
            }
        }
        return res;
    }
};
~~~

**解答2:**
~~~cpp
//faster
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        std::vector<int> res;
        int left = 0;
        int right = nums.size() - 1;
        while(left < right)
        {
            if(nums[left] + nums[right] == target)
            {
                res.push_back(nums[left]);
                res.push_back(nums[right]);
                return res;
            }
            if(nums[left] + nums[right] > target)
                right--;
            else
                left++;
        }
        return res;
    }
};
~~~


# <a name="57-II">57-II. 和为s的连续正数序列</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

输入一个正整数 target ，输出所有和为 target 的连续正整数序列（至少含有两个数）。

序列内的数字由小到大排列，不同序列按照首个数字从小到大排列。

**示例 1:**
~~~
输入：target = 9
输出：[[2,3,4],[4,5]]
~~~
**示例 2:**
~~~
输入：target = 15
输出：[[1,2,3,4,5],[4,5,6],[7,8]]
~~~

**限制：**

* 1 <= target <= 10^5

**解答1:**
~~~cpp
class Solution {
public:
    vector<vector<int>> findContinuousSequence(int target) {
        int left = 1,right = 1;
        std::vector<std::vector<int>> res;
        while(right <= ((target >> 1) + 1))
        {
            int tmp = (left + right)*(right - left + 1);
            if(tmp == 2*target)
            {
                std::vector<int> subres;
                for(int i = left;i <= right;i++)
                {
                    subres.push_back(i);
                }
                res.push_back(subres);
                left++;
            }
            else if(tmp < 2*target)
                right++;
            else 
                left++;
        }
        return res;
    }
};
~~~


# <a name="58-I">58-I. 翻转单词顺序</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

输入一个英文句子，翻转句子中单词的顺序，但单词内字符的顺序不变。为简单起见，标点符号和普通字母一样处理。例如输入字符串"I am a student. "，则输出"student. a am I"。

**示例 1:**
~~~
输入: "the sky is blue"
输出: "blue is sky the"
~~~
**示例 2:**
~~~
输入: "  hello world!  "
输出: "world! hello"
解释: 输入字符串可以在前面或者后面包含多余的空格，但是反转后的字符不能包括。
~~~
**示例 3:**
~~~
输入: "a good   example"
输出: "example good a"
解释: 如果两个单词间有多余的空格，将反转后单词间的空格减少到只含一个。
~~~

**说明：**

* 无空格字符构成一个单词。
* 输入字符串可以在前面或者后面包含多余的空格，但是反转后的字符不能包括。
* 如果两个单词间有多余的空格，将反转后单词间的空格减少到只含一个。

**解答1:**
~~~cpp
class Solution {
public:
    string reverseWords(string s) {
        std::string res;
        if(s.empty()) return res;
        int len = s.size();
        int left = len - 1,right = len - 1;
        while(left > -1)
        {
            while(s[right] == ' ')
            {
                left--;
                right--;
                if(left < 0) return res.substr(0,res.size() - 1);
            }
            while(left > -1 &&  s[left] != ' ' )
            {
                left--;
            }
            res.append(s.substr(left + 1,right-left));
            res.append(" ");
            right = left;
        }
        res = res.substr(0,res.size() - 1);
        return res;
    }
};
~~~


# <a name="58-II">58-II. 左旋转字符串</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

字符串的左旋转操作是把字符串前面的若干个字符转移到字符串的尾部。请定义一个函数实现字符串左旋转操作的功能。比如，输入字符串"abcdefg"和数字2，该函数将返回左旋转两位得到的结果"cdefgab"。

**示例 1:**
~~~
输入: s = "abcdefg", k = 2
输出: "cdefgab"
~~~
**示例 2:**
~~~
输入: s = "lrloseumgh", k = 6
输出: "umghlrlose
~~~


**说明：**

* 1 <= k < s.length <= 10000

**解答1:**
~~~cpp
class Solution {
public:
    string reverseLeftWords(string s, int n) {
        return s.substr(n,s.size()-n) + s.substr(0,n);
    }
};
~~~


# <a name="59-I">59.I. 滑动窗口的最大值</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

给定一个数组 nums 和滑动窗口的大小 k，请找出所有滑动窗口里的最大值


**示例1：**
~~~
输入: nums = [1,3,-1,-3,5,3,6,7], 和 k = 3
输出: [3,3,5,5,6,7] 
解释: 

  滑动窗口的位置                最大值
---------------               -----
[1  3  -1] -3  5  3  6  7       3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7
~~~

**提示：**

你可以假设 k 总是有效的，在输入数组不为空的情况下，1 ≤ k ≤ 输入数组的大小。

**解答1:**
~~~cpp
class Solution {
public:
    vector<int> maxSlidingWindow(vector<int>& nums, int k) {
        if(nums.empty()) return {};
        std::vector<int> res(nums.size()-k+1);
        for(int idx = 0;idx < res.size();idx++)
        {
            res[idx] = INT_MIN;
            for(int i = idx;i < idx + k;i++)
            {
                if(nums[i] > res[idx]) res[idx] = nums[i];
            }
        }
        return res;
    }
};
~~~

**解答2:**
~~~cpp
class Solution {
public:
    vector<int> maxSlidingWindow(vector<int>& nums, int k) {
        vector<int> ans;
        deque<int> deq;
        int n = nums.size();
        for (int i = 0; i < n; i++){
            while(!deq.empty() && nums[i] > nums[deq.back()]){
                deq.pop_back();
            }
            if (!deq.empty() && deq.front() < i - k + 1) deq.pop_front();
            deq.push_back(i);
            if (i >= k -1) ans.push_back(nums[deq.front()]);
        }
        return ans;

    }
};
~~~


# <a name="59-II">59.II. 队列的最大值</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

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

**示例2：**
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

# <a name="60">60. n个骰子的点数</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

把n个骰子扔在地上，所有骰子朝上一面的点数之和为s。输入n，打印出s的所有可能的值出现的概率。

你需要用一个浮点数数组返回答案，其中第 i 个元素代表这 n 个骰子所能掷出的点数集合中第 i 小的那个的概率。

**示例1：**
~~~
输入: 1
输出: [0.16667,0.16667,0.16667,0.16667,0.16667,0.16667]
~~~

**示例2：**
~~~
输入: 2
输出: [0.02778,0.05556,0.08333,0.11111,0.13889,0.16667,0.13889,0.11111,0.08333,0.05556,0.02778]

~~~

**限制：**

0 <= 数组长度 <= 10^5

**解答1:**
~~~cpp
public:
    vector<double> twoSum(int n) {
        int res[70] = {0};
        int all = 6;
        for(int i = 1;i < 7;i++) res[i] = 1;
        for(int j = 1;j < n;j++)
        {
            for(int k = 6*(j+1);k > j;k--)
            {
                res[k] = 0;
                for(int step = 1;step < 7 && k-step > j-1;step++)
                {
                    res[k] += res[k-step];
                }
            }
            all *= 6;
        }
        std::vector<double> ret;
        for(int idx = n;idx < 6*n + 1;idx++)
        {
            ret.push_back(double(res[idx])/all);
        }
        return ret;
    }
};
~~~


# <a name="61">61. 扑克牌中的顺子</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

从扑克牌中随机抽5张牌，判断是不是一个顺子，即这5张牌是不是连续的。2～10为数字本身，A为1，J为11，Q为12，K为13，而大、小王为 0 ，可以看成任意数字。A 不能视为 14。

**示例1：**
~~~
输入: [1,2,3,4,5]
输出: True
~~~

**示例2：**
~~~
输入: [0,0,1,2,5]
输出: True
~~~

**限制：**

数组长度为 5 

数组的数取值为 [0, 13] .

**解答1:**
~~~cpp
class Solution {
public:
    bool isStraight(vector<int>& nums) {
        int valid = 0;
        int min = INT_MAX;
        int max = INT_MIN;
        std::unordered_map<int,int> mymap;
        for(int i = 0;i < nums.size();i++)
        {
            if(nums[i] == 0)
            {
                valid++;
                continue;
            }
            if(mymap.find(nums[i])==mymap.end())
            {
                valid++;
                mymap[nums[i]] = i;
                if(nums[i] < min) min = nums[i];
                if(nums[i] > max) max = nums[i];
            }
        }
        if(valid==5 && (max-min<5)) return true;
        else return false;
    }
};
~~~


# <a name="62">62. 圆圈中最后剩下的数字</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

0,1,,n-1这n个数字排成一个圆圈，从数字0开始，每次从这个圆圈里删除第m个数字。求出这个圆圈里剩下的最后一个数字。

例如，0、1、2、3、4这5个数字组成一个圆圈，从数字0开始每次删除第3个数字，则删除的前4个数字依次是2、0、4、1，因此最后剩下的数字是3。

**示例1：**
~~~
输入: n = 5, m = 3
输出: 3
~~~

**示例2：**
~~~
输入: n = 10, m = 17
输出: 2
~~~

**限制：**

* 1 <= n <= 10^5
* 1 <= m <= 10^6

**解答1:**
~~~cpp
//over time limit
class Solution {
public:
    int lastRemaining(int n, int m) {
        std::vector<int> vec;
        for(int i = 0;i < n;i++) vec.push_back(i);
        int idx = 0;
        for(int i = 0;i < n - 1;i++)
        {
            int len = vec.size();
            idx = (idx + (m - 1)) % len;
            vec.erase(vec.begin() + idx);
        }
        return vec[0];
    }
};
~~~

**解答2:**
~~~cpp
class Solution {
public:
    int lastRemaining(int n, int m) {
        int ans = 0;
        for(int i = 2;i < n + 1;i++)
            ans = (ans + m) % i;
        return ans;
    }
};
~~~


# <a name="63">63. 股票的最大利润</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

假设把某股票的价格按照时间先后顺序存储在数组中，请问买卖该股票一次可能获得的最大利润是多少？

**示例1：**
~~~
输入: [7,1,5,3,6,4]
输出: 5
解释: 在第 2 天（股票价格 = 1）的时候买入，在第 5 天（股票价格 = 6）的时候卖出，最大利润 = 6-1 = 5 。
     注意利润不能是 7-1 = 6, 因为卖出价格需要大于买入价格。

~~~

**示例2：**
~~~
输入: [7,6,4,3,1]
输出: 0
解释: 在这种情况下, 没有交易完成, 所以最大利润为 0。
~~~

**限制：**

0 <= 数组长度 <= 10^5

**解答1:**
~~~cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int max = 0;
        int min_cost = INT_MAX;
        for(int i = 0 ;i < prices.size();i++)
        {
            if(prices[i] < min_cost) min_cost = prices[i];
            max = prices[i] - min_cost > max? prices[i] - min_cost : max;
        }
        return max;
    }
};
~~~


# <a name="64">64. 求1+2+…+n</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

求 1+2+...+n ，要求不能使用乘除法、for、while、if、else、switch、case等关键字及条件判断语句（A?B:C）。

**示例1：**
~~~
输入: n = 3
输出: 6
~~~

**示例2：**
~~~
输入: n = 9
输出: 45
~~~

**限制：**

1 <= n <= 10000

**解答1:**
~~~cpp
// &&短路 n==false时不运行后续操作
class Solution {
public:
    int sumNums(int n) {
        int res = n;
        n && (res+=sumNums(n-1));
        return res;
    }
};
~~~

**解答2:**
~~~cpp
class Solution {
public:
    int sumNums(int n) {
        bool arr[n][n + 1];
        return sizeof(arr)>>1;
    }
};
~~~


# <a name="65">65. 不用加减乘除做加法</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

写一个函数，求两个整数之和，要求在函数体内不得使用 “+”、“-”、“*”、“/” 四则运算符号。

**示例1：**
~~~
输入: a = 1, b = 1
输出: 2
~~~


**限制：**

* a, b 均可能是负数或 0
* 结果不会溢出 32 位整数

**解答1:**
~~~cpp
class Solution {
public:
    int add(int a, int b) {
        int res = a^b;
        int ov = (unsigned int)(a&b)<<1;
        while(ov)
        {
            int tmp = res;
            res = res ^ ov;
            ov = (unsigned int)(tmp & ov) << 1;
        }
        return res;
    }
};
~~~


# <a name="66">66. 构建乘积数组</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

给定一个数组 A[0,1,…,n-1]，请构建一个数组 B[0,1,…,n-1]，其中 B 中的元素 B[i]=A[0]×A[1]×…×A[i-1]×A[i+1]×…×A[n-1]。不能使用除法。


**示例1：**
~~~
输入: [1,2,3,4,5]
输出: [120,60,40,30,24]
~~~


**限制：**

* 所有元素乘积之和不会溢出 32 位整数
* a.length <= 100000

**解答1:**
~~~cpp
class Solution {
public:
    vector<int> constructArr(vector<int>& a) {
        std::vector<int> res(a.size(),1);
        for(int i = 1;i<a.size();i++)
        {
            res[i] = res[i-1]*a[i-1];
        }
        int tmp = 1;
        for(int i = a.size()-2;i > -1;i--)
        {
            tmp *= a[i+1];
            res[i] *= tmp;
        }
        return res;
    }
};
~~~



# <a name="68-I">68-I. 二叉搜索树的最近公共祖先</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

给定一个二叉搜索树, 找到该树中两个指定节点的最近公共祖先。

最近公共祖先的定义为：对于有根树 T 的两个结点 p、q，最近公共祖先表示为一个结点 x，满足 x 是 p、q 的祖先且 x 的深度尽可能大(一个节点也可以是它自己的祖先)

例如，给定如下二叉搜索树:  root = [6,2,8,0,4,7,9,null,null,3,5]

![eg](img/68-I.png)

**示例1：**
~~~
输入: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 8
输出: 6 
解释: 节点 2 和节点 8 的最近公共祖先是 6。
~~~

**示例2：**
~~~
输入: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 4
输出: 2
解释: 节点 2 和节点 4 的最近公共祖先是 2, 因为根据定义最近公共祖先节点可以为节点本身。
~~~

**限制：**

* 所有节点的值都是唯一的。
* p、q 为不同节点且均存在于给定的二叉搜索树中。

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
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if((root->val - q->val)*(root->val - p->val) <= 0) return root;
        else if(root->val < q->val) return lowestCommonAncestor(root->right, p, q);
        else return lowestCommonAncestor(root->left, p, q);
    }
};
~~~




# <a name="68-II">68-II. 二叉树的最近公共祖先</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

**题目描述**

给定一个二叉树, 找到该树中两个指定节点的最近公共祖先。

最近公共祖先的定义为：对于有根树 T 的两个结点 p、q，最近公共祖先表示为一个结点 x，满足 x 是 p、q 的祖先且 x 的深度尽可能大(一个节点也可以是它自己的祖先)

例如，给定如下二叉树:  root = [3,5,1,6,2,0,8,null,null,7,4]

![eg](img/68-II.png)

**示例1：**
~~~
输入: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1
输出: 3
解释: 节点 5 和节点 1 的最近公共祖先是节点 3。
~~~

**示例2：**
~~~
输入: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4
输出: 5
解释: 节点 5 和节点 4 的最近公共祖先是节点 5。因为根据定义最近公共祖先节点可以为节点本身。
~~~

**限制：**

* 所有节点的值都是唯一的。
* p、q 为不同节点且均存在于给定的二叉树中。

**解答1:**
~~~cpp
//1548ms
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
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if(root->val == p->val || root->val == q->val) return root;
        if(insubtree(root->left,p)&&insubtree(root->left,q)) 
            return lowestCommonAncestor(root->left,p,q);
        if(insubtree(root->right,p)&&insubtree(root->right,q))
            return lowestCommonAncestor(root->right,p,q);
        else return root;
    }
    bool insubtree(TreeNode* root,TreeNode* target)
    {
        if(root == nullptr) return false;
        if(root->val == target->val) return true;
        else return insubtree(root->left,target) || insubtree(root->right,target);
    }
};
~~~

**解答2:**
~~~cpp
//28ms
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
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if(root == nullptr ||root->val == p->val || root->val == q->val) return root;
        TreeNode* left = lowestCommonAncestor(root->left,p,q);
        TreeNode* right = lowestCommonAncestor(root->right,p,q);
        if(left == nullptr) return right;
        if(right == nullptr) return left;
        return root;
    }
};
~~~