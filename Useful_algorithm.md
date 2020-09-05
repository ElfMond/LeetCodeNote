# DFS search

~~~cpp
#include <iostream>
#include <vector>

std::vector<std::vector<int>> matrix;
std::vector<std::vector<int>> currpath;
std::vector<std::vector<int>> bestpath;

void findpath(int i,int j)
{
    int n = matrix.size();
    int m = matrix[0].size();
    if(i < 0 || j < 0 || i >= n || j >= m || matrix[i][j]) return; 
    matrix[i][j] = 1;   //set visited
    currpath.push_back({i,j});  //push path
    if(i == n - 1 && j == m - 1)    //found endpoint
    {
        if (bestpath.empty() || currpath.size() < bestpath.size())
            bestpath = currpath;
    }
    findpath(i - 1,j);  //try 4 directions
    findpath(i + 1,j);
    findpath(i,j - 1);
    findpath(i,j + 1);

    matrix[i][j] = 0;   //recover visted to false
    currpath.pop_back();    //delete path
}


int main()
{
    int n;
    int m;

    while(std::cin>>n>>m)
    {
        matrix = std::vector<std::vector<int>>(n,std::vector<int>(m,0));
        currpath.clear();
        bestpath.clear();
        for(int i = 0;i < n;i++)
        {
            for(int j = 0;j < m;j++)
            {
                std::cin>>matrix[i][j];
            }
        }
        findpath(0,0);
        for(int l = 0;l < bestpath.size();l++)
        {
            std::cout<<'('<<bestpath[l][0]<<','<<bestpath[l][1]<<')'<<'\n';
        }
    }
    return 0;
}
~~~