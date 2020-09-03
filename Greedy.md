# [1] 455. 数组中的第K个最大元素
[leetcode: Nr.167](https://leetcode-cn.com/problems/assign-cookies/) (easy)

假设你是一位很棒的家长，想要给你的孩子们一些小饼干。但是，每个孩子最多只能给一块饼干。对每个孩子 i ，都有一个胃口值 gi ，这是能让孩子们满足胃口的饼干的最小尺寸；并且每块饼干 j ，都有一个尺寸 sj 。如果 sj >= gi ，我们可以将这个饼干 j 分配给孩子 i ，这个孩子会得到满足。你的目标是尽可能满足越多数量的孩子，并输出这个最大数值。

**注意：**

你可以假设胃口值为正。
一个小朋友最多只能拥有一块饼干。

**示例 1:**
~~~
输入: [1,2,3], [1,1]

输出: 1

解释: 
你有三个孩子和两块小饼干，3个孩子的胃口值分别是：1,2,3。
虽然你有两块小饼干，由于他们的尺寸都是1，你只能让胃口值是1的孩子满足。
所以你应该输出1。
~~~
**示例 2:**
~~~
输入: [1,2], [1,2,3]

输出: 2

解释: 
你有两个孩子和三块小饼干，2个孩子的胃口值分别是1,2。
你拥有的饼干数量和尺寸都足以让所有孩子满足。
所以你应该输出2.
~~~

**My Solution**
~~~cpp
class Solution {
public:
    int findContentChildren(vector<int>& g, vector<int>& s) {
        int res = 0;
        std::sort(g.begin(),g.end());
        std::sort(s.begin(),s.end());
        int gidx = 0;
        int sidx = 0;
        while(  gidx < g.size() && sidx < s.size() )
        {
            if(g[gidx] <= s[sidx])
            {
                res++;
                gidx++;
                sidx++;
            }
            else sidx++;
        }
        return res;
    }
};
~~~


# [2] 435. 无重叠区间
[leetcode: Nr.435](https://leetcode-cn.com/problems/non-overlapping-intervals/) (medium)

给定一个区间的集合，找到需要移除区间的最小数量，使剩余区间互不重叠。

**注意:**

可以认为区间的终点总是大于它的起点。
区间 [1,2] 和 [2,3] 的边界相互“接触”，但没有相互重叠。

**示例 1:**
~~~
输入: [ [1,2], [2,3], [3,4], [1,3] ]

输出: 1

解释: 移除 [1,3] 后，剩下的区间没有重叠。
~~~
**示例 2:**
~~~
输入: [ [1,2], [1,2], [1,2] ]

输出: 2

解释: 你需要移除两个 [1,2] 来使剩下的区间没有重叠。
~~~
**示例 3:**
~~~
输入: [ [1,2], [2,3] ]

输出: 0

解释: 你不需要移除任何区间，因为它们已经是无重叠的了。
~~~

**My Solution**
~~~cpp
//Dynamic Programming
class Solution {
public:
    int eraseOverlapIntervals(vector<vector<int>>& intervals) {
        if(intervals.size()==0) return 0;
        std::sort(intervals.begin(),intervals.end(),[](std::vector<int>&a,std::vector<int>&b) {return a[0]<b[0];});
        std::vector<int> dp(intervals.size(),0);
        dp[0] = 1;
        for(int i = 1;i<intervals.size();i++)
        {
            for(int j = i-1;j>-1;j--)
            {
                if(ov(intervals[i],intervals[j])) dp[i] = dp[i]<dp[j]? dp[j]:dp[i];
                else 
                {
                    dp[i] = dp[i]<(dp[j]+1) ? dp[j]+1:dp[i];
                    break;
                }
            }
        }
        return intervals.size()-dp[intervals.size()-1];
    }
    bool ov(std::vector<int>a,std::vector<int>b)
    {
        if(a[0]>=b[0] && a[0] < b[1]) return true;
        if(a[1]>b[0] && a[1] <= b[1]) return true;
        if(b[0]>=a[0] && b[0] < a[1]) return true;
        if(b[1]>a[0] && b[1] <= a[1]) return true;
        return false;
    }
};
~~~
~~~cpp
//Greedy
class Solution {
public:
    int eraseOverlapIntervals(vector<vector<int>>& intervals) {
        int res = 0;
        if(intervals.size()==0) return res;
        std::sort(intervals.begin(),intervals.end(),[](std::vector<int>&a,std::vector<int>&b) {return a[0]<b[0];});
        int pre = 0;
        res++;
        for(int i = 1;i<intervals.size();i++)
        {
            if(ov(intervals[i],intervals[pre]))
            {
                if(intervals[i][1]<intervals[pre][1]) pre = i;
            }
            else
            {
                pre = i;
                res++;
            }
        }
        return intervals.size()-res;
    }
    bool ov(std::vector<int>&a,std::vector<int>&b)
    {
        if(a[0]>=b[0] && a[0] < b[1]) return true;
        if(a[1]>b[0] && a[1] <= b[1]) return true;
        if(b[0]>=a[0] && b[0] < a[1]) return true;
        if(b[1]>a[0] && b[1] <= a[1]) return true;
        return false;
    }
};
~~~

# [3] 452. 用最少数量的箭引爆气球
[leetcode: Nr.452](https://leetcode-cn.com/problems/minimum-number-of-arrows-to-burst-balloons/) (medium)

在二维空间中有许多球形的气球。对于每个气球，提供的输入是水平方向上，气球直径的开始和结束坐标。由于它是水平的，所以y坐标并不重要，因此只要知道开始和结束的x坐标就足够了。开始坐标总是小于结束坐标。平面内最多存在104个气球。

一支弓箭可以沿着x轴从不同点完全垂直地射出。在坐标x处射出一支箭，若有一个气球的直径的开始和结束坐标为 xstart，xend， 且满足  xstart ≤ x ≤ xend，则该气球会被引爆。可以射出的弓箭的数量没有限制。 弓箭一旦被射出之后，可以无限地前进。我们想找到使得所有气球全部被引爆，所需的弓箭的最小数量。

**Example:**
~~~
输入:
[[10,16], [2,8], [1,6], [7,12]]

输出:
2

解释:
对于该样例，我们可以在x = 6（射爆[2,8],[1,6]两个气球）和 x = 11（射爆另外两个气球）。
~~~

**My Solution**
~~~cpp
//Dynamic Programming
class Solution {
public:
    int findMinArrowShots(vector<vector<int>>& points) {
        if(points.size()==0) return 0;
        std::sort(points.begin(),points.end(),[](std::vector<int>&a,std::vector<int>&b){return a[0]<b[0];});
        std::vector<int> dp(points.size(),0);
        dp[0] = 1;
        for(int i = 1;i<points.size();i++)
        {
            for(int j = i-1;j>-1;j--)
            {
                if(ov(points[j],points[i])) dp[i] = dp[j];
                else 
                {
                    dp[i] = dp[j]+1;
                    break;
                }
            }
        }
        return dp[points.size()-1];
    }
    bool ov(std::vector<int>&a,std::vector<int>&b)
    {
        if(a[0]>=b[0] && a[0] <= b[1]) return true;
        if(a[1]>=b[0] && a[1] <= b[1]) return true;
        if(b[0]>=a[0] && b[0] <= a[1]) return true;
        if(b[1]>=a[0] && b[1] <= a[1]) return true;
        return false;
    }
};
~~~

~~~cpp
//Greedy
class Solution {
public:
    int findMinArrowShots(vector<vector<int>>& points) {
        if(points.size()==0) return 0;
        std::sort(points.begin(),points.end(),[](std::vector<int>&a,std::vector<int>&b){return a[1]<b[1];});
        int res = 1;
        int arrpos = points[0][1];
        for(int i = 1;i<points.size();i++)
        {
            if(points[i][0] > arrpos)
            {
                res++;
                arrpos = points[i][1];
            }
        }
        return res;
    }
};
~~~

# [4] 406. 根据身高重建队列
[leetcode: Nr.452](https://leetcode-cn.com/problems/queue-reconstruction-by-height/) (medium)

假设有打乱顺序的一群人站成一个队列。 每个人由一个整数对(h, k)表示，其中h是这个人的身高，k是排在这个人前面且身高大于或等于h的人数。 编写一个算法来重建这个队列。

注意：
总人数少于1100人。

**示例**
~~~
输入:
[[7,0], [4,4], [7,1], [5,0], [6,1], [5,2]]

输出:
[[5,0], [7,0], [5,2], [6,1], [4,4], [7,1]]
~~~

**My Solution**
~~~cpp
class Solution {
public:
    vector<vector<int>> reconstructQueue(vector<vector<int>>& people) {
        std::vector<std::vector<int>> res(people.size(),std::vector<int>(2,0));
        std::vector<int> loc(people.size(),0);
        std::sort(people.begin(),people.end(),[](std::vector<int>&a,std::vector<int>&b)
        {
            if(a[0]<b[0]) return a[0]<b[0];
            else if(a[0]==b[0]) return a[1]>b[1];
            return false;
        });
        for(int i = 0;i < people.size();i++)
        {
            int rank = people[i][1]+1;
            int pos = 0;
            while(rank)
            {
                if(loc[pos]) pos++;
                else
                {
                    pos++;
                    rank--;
                }
            }
            res[pos-1] = people[i];
            loc[pos-1] = 1;
        }
        return res;
    }
};
~~~